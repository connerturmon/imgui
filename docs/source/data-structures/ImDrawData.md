# ImDrawData
```
struct ImDrawData
{
    // Fields
    bool            Valid;
    ImDrawList**    CmdLists;
    int             CmdListsCount;
    int             TotalIdxCount;
    int             TotalVtxCount;
    ImVec2          DisplayPos;
    ImVec2          DisplaySize;
    ImVec2          FramebufferScale;

    // Constructor / Destructor
    ImDrawData()    { Valid = false; Clear(); }
    ~ImDrawData()   { Clear(); }

    // Functions
    void Clear()    {
        Valid = false;
        CmdLists = NULL;
        CmdListsCount = TotalVtxCount = TotalIdxCount = 0;
        DisplayPos = DisplaySize = FramebufferScale = ImVec2(0.f, 0.f); }
    IMGUI_API void  DeIndexAllBuffers();
    IMGUI_API void  ScaleClipRects(const ImVec2& fb_scale);
};
```
All draw data to render a __ImGui__ frame.

All draw command lists required to render the frame + pos/size coordinates to use for the projection matrix.

## Additionals
The style and the naming convention here is a little inconsistent, we currently preserve them for backwards compatibility purposes, as this is one of the oldest structures exposed by the library! Basically, `ImDrawList` == `CmdList`.