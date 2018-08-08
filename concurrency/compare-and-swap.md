# Compare and Swap

IA32, Sparc 같은 프로세서에서 채택하고 있는 방법은 비교 후 치환\(CAS\) 명령을 제공하는 방법이다.

만약 여러 스레드가 동시에 CAS 연산을 사용해 한 변수의 값을 변경하려고 하면, 스레드 가운데 하나만 성공적으로 값을 변경하고 나머지 스레드는 모두 실패한다.

자바에서 하드웨어 프로세서의 지원을 통한 CAS 연산을 하려면 Atomic series로 호출해주면된다.

내부 구현은 Unsafe Class 의 compareAndSwap시리즈로 구현 되어 있다.

[jdk8/jdk8/hotspot: 87ee5ee27509 /hg.openjdk.java.net](http://hg.openjdk.java.net/jdk8/jdk8/hotspot/file/87ee5ee27509)

```cpp
UNSAFE_ENTRY(jboolean, Unsafe_CompareAndSwapObject(JNIEnv *env, jobject unsafe, jobject obj, jlong offset, jobject e_h, jobject x_h))
  UnsafeWrapper("Unsafe_CompareAndSwapObject");
  oop x = JNIHandles::resolve(x_h);
  oop e = JNIHandles::resolve(e_h);
  oop p = JNIHandles::resolve(obj);
  HeapWord* addr = (HeapWord *)index_oop_from_field_offset_long(p, offset);
  if (UseCompressedOops) {
    update_barrier_set_pre((narrowOop*)addr, e);
  } else {
    update_barrier_set_pre((oop*)addr, e);
  }
  oop res = oopDesc::atomic_compare_exchange_oop(x, addr, e);
  jboolean success  = (res == e);
  if (success)
    update_barrier_set((void*)addr, x);
  return success;
UNSAFE_END
```

