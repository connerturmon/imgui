# Vectors
There are two ImGui Vector classes used for storing various x, y, z, and w values:  
`ImVec2` and `ImVec4`.

Both Vector data types share a `IM_VEC*_CLASS_EXTRA` preprocessor macro that allows the user to define additional constructors and implicit cast operators in `imconfig.h` in order to convert back and forth between user math types and `ImVec*` types.

Vectors will be initialized to 0.0f if no values for the x, y, z, or w values are provided.

## ImVec2
```
struct ImVec2
{
    float                                   x, y;
    ImVec2()                                { x = y = 0.0f; }
    ImVec2(float _x, float _y)              { x = _x; y = _y; }
    float  operator[] (size_t idx) const    { IM_ASSERT(idx <= 1); return (&x)[idx]; }    // We very rarely use this [] operator, the assert overhead is fine.
    float& operator[] (size_t idx)          { IM_ASSERT(idx <= 1); return (&x)[idx]; }    // We very rarely use this [] operator, the assert overhead is fine.
#ifdef IM_VEC2_CLASS_EXTRA
    IM_VEC2_CLASS_EXTRA     // Define additional constructors and implicit cast operators in imconfig.h to convert back and forth between your math types and ImVec2.
#endif
};
```

## ImVec4
```
struct ImVec4
{
    float                                   x, y, z, w;
    ImVec4()                                { x = y = z = w = 0.0f; }
    ImVec4(float _x, float _y, float _z, float _w)  { x = _x; y = _y; z = _z; w = _w; }
#ifdef IM_VEC4_CLASS_EXTRA
    IM_VEC4_CLASS_EXTRA     // Define additional constructors and implicit cast operators in imconfig.h to convert back and forth between your math types and ImVec4.
#endif
};
```