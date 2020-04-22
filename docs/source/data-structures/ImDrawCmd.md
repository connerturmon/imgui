# ImDrawCmd
```
struct ImDrawCmd
{
    // Fields
    unsigned int    ElemCount;
    ImVec4          ClipRect;
    ImTextureID     TextureId;
    unsigned int    VtxOffset;
    unsigned int    IdxOffset;
    ImDrawCallback  UserCallback;
    void*           UserCallbackData;
    
    // Constructor
    ImDrawCmd() {
        ElemCount = 0;
        TextureId = (ImTextureID)NULL;
        VtxOffset = IdxOffset = 0;
        UserCallback = NULL;
        UserCallbackData = NULL; }
};
```
A single draw command within a parent ImDrawList (generally maps to 1 GPU draw call, unless it is a callback). Pre __ImGui 1.71__ back-ends will typically ignore the `VtxOffset`/`IdxOffset` fields.

When `io.BackendFlags & ImGuiBackendFlags_RendererHasVtxOffset` is enabled, those fields allow us to render meshes larger than 64K vertices while keeping 16-bit indices.

## Fields
```
unsigned int ElemCount;
```
Number of indices (multiple of 3) to be rendered as triangles. Vertices are stored in the callee [`ImDrawList`](#imdrawlist)'s `vtx_buffer[]` array, indices in `idx_buffer[]`.


```
ImVec4 ClipRect;
```
Clipping rectangle `(x1, y1, x2, y2)`. Subtract `ImDrawData->DisplayPos` to get clipping rectangle in "viewport" coordinates.


```
ImTextureID TextureId;
```
User-provided texture ID. Set by user in `ImfontAtlas::SetTexID()` for fonts or passed to `Image*()` functions. Ignore if never using images or multiple fonts atlas.


```
unsigned int VtxOffset;
```
Start offset in vertex buffer. __Pre-1.71__ or without `ImGuiBackendFlags_RendererHasVtxOffset` always 0. With `ImGuiBackendFlags_RendererHasVtxOffset` may be greater than 0 to support meshes larger than 64K vertices with 16-bit indices.


```
unsigned int IdxOffset;
```
Start offset in index buffer. Always equal to sum of `ElemCount` drawn so far.


```
ImDrawCallback UserCallback
```
`if != NULL`, call the function instead of rendering the vertices. `clip_rect` and `texture_id` will be set normally.


```
void UserCallbackData;
```
The draw callback code can access this.

## Constructor
```
ImDrawCmd() {
        ElemCount = 0;
        TextureId = (ImTextureID)NULL;
        VtxOffset = IdxOffset = 0;
        UserCallback = NULL;
        UserCallbackData = NULL; }
```