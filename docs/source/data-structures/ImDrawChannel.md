# ImDrawChannel
```
struct ImDrawChannel
{
    // Fields
    ImVector<ImDrawCmd>         _CmdBuffer;
    ImVector<ImDrawIdx>         _IdxBuffer;
};
```
Temporary storage to output draw commands out of order, __used by__ `ImDrawListSplitter` __and__ `ImDrawList::ChannelsSplit()`

## Fields
```
ImVector<ImDrawCmd> _CmdBuffer;
```
ImGui vector data structure that contains a buffer of all `ImDrawCmd`s to draw.

```
ImVector<ImDrawIdx> _IdxBuffer;
```
ImGui vector data structure that contains the indices of `ImDrawCmd`s to draw.