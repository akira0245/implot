The list below represents a combination of high-priority work, nice-to-have features, and random ideas. We make no guarantees that all of this work will be completed or even started. If you see something that you need or would like to have, let us know, or better yet consider submitting a PR for the feature.

## API

- make BeginPlot take fewer args:
    ```cpp
    if (ImPlot::BeginPlot("MyPlot",p_flags,size)) {
        ImPlot::Axis(ImAxis_X1,"X",x_flags);
        ImPlot::Axis(ImAxis_Y1,"Y",y_flags);
        ImPlot::AxisLimits(ImAxis_X1, 0, 10);
        ImPlot::AxisFormat(ImAxis_Y1, "%.3f$");
        ImPlot::AxisTicks(ImAxis_Y1, ...);
        ImPlot::AxisLink(ImAxis_X1, ....);        
        ImPlot::Legend(loc,orn,l_flags);
        ...        
        ImPlot::PlotLine(...);
        ImPlot::EndPlot();
    }
    ```
    - add shortcut/legacy overloads

## Axes

- add support for multiple x-axes and don't limit count to 3
    - will require `SetupNextAxis` API
- make axis side configurable (top/left, right/bottom) via new flag `ImPlotAxisFlags_Opposite`
- add support for setting tick label strings via callback
- add flag to remove weekends on Time axis
- pixel space scale, normalized space scale (see matplotlib)
- give each axis an ID, remove ad-hoc DND solution
- make ImPlotFlags_Equal not a flag -> `SetupEqual(ImAxis x, ImAxis y)`
- allow axis to be drag to opposite side (ala ImGui Table headers)
- allow inverted arguments `SetAxes` to transpose data?

## Plot Items

- add `ImPlotLineFlags`, `ImPlotBarsFlags`, etc. for each plot type
- add `PlotBarGroups` wrapper that makes rendering groups of bars easier
- add `PlotBubbles` (see MATLAB bubble chart)
- add non-zero references for `PlotBars` etc.
- add exploding to `PlotPieChart` (on hover-highlight?)

## Styling

- support gradient and/or colormap sampled fills (e.g. ImPlotFillStyle_)
- add hover/active color for plot axes
- API for setting different fonts for plot elements

## Colormaps

- gradient editing tool
- `RemoveColormap`

## Legend

- `ImPlotLegendFlags`
    - `_SortItems`
    - `_Scroll`
    - `_NoButtons`
- improve legend icons (e.g. adopt markers, gradients, etc)
- make legend frame use ButtonBehavior

## Tools / Misc.

- add `IsPlotChanging` to detect change in limits
- add ability to extend plot/axis context menus
- add LTTB downsampling for lines
- remove tag from drag line/point -> add `AxisTag` tool
- add box selection to axes
- fix frame delay on DragX tools
- first frame render delay might fix "fit pop" effect
- `SetupAxisColor()`
- `SetupAxisConstraints()`
- `SetupAxisHome()`   

## Optimizations

- find faster way to buffer data into ImDrawList (very slow)
- reduce number of calls to `PushClipRect`
- explore SIMD operations for high density plot items

## Bugs

- legend items can be hovered even if plot is not
- change colormap not working demo


## Completed
- make query a tool -> `DragRect`
- rework DragLine/Point to use ButtonBehavior
