# [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) <!-- omit in toc -->

A representation of a generic raw binary data buffer. You cannot manipulate the data within directly.

# Example

```js
const a = new ArrayBuffer(8);
const a8 = new Uint8Array(a);
const a16 = new Uint16Array(a);
const a32 = new Uint32Array(a);
a8[0] = 0x11;
a8[1] = 0x22;
a16[1] = 0x3344;
a32[1] = 0x55667788;

/* On my system: (because little endian)
> a
ArrayBuffer {
  [Uint8Contents]: <11 22 44 33 88 77 66 55>,
  byteLength: 8
}
*/
```
