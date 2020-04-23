# Visualization

| Function  | Description                    |
| ------------- | ------------------------------ |
| `generate_color()`      | Generates a random color.       |
| `rgb()`   | Return a tuple of integers, as used in AWT/Java plots.   |
| `hex_rgb()`      | Return a hex string, as used in Tk plots.       |
| `cmap_hex_color()`   | Convert a Colormap to hex color.   |
| `add_map_legend()`   | ?   |
| `save_map()`      | Save a visualization in a map in a new file.       |
| `save_wkt()`   | Save a visualization in a map in a new file .wkt.   |
| `show_object_id_by_date()`      | Generates four visualizations based on datetime feature day periods, day of the week, date and hours of the day.      |
| `show_lat_lon_gps()`   | Generate a visualization with points [lat, lon] of dataset.   |
| `create_base_map()`      | Generates a Folium map.       |
| `heatmap()`   | Generate visualization of Heat Map using folium plugin.  |
| `cluster()`      | Generate visualization of Marker Cluster using folium plugin.      |
| `faster_cluster()`   |Generate visualization of Faster Cluster using folium plugin.  |
| `plot_markers()`      | Plot markers of Folium on map.     |
| `plot_trajectories_with_folium()`   | Generate visualization of all trajectories with folium.   |
| `plot_trajectory_by_id_with_folium()`      | Generate visualization of trajectory with the id provided by user.       |
| `plot_trajectory_by_period()`   | Generate trajectory view by period of day provided by user.   |
| `plot_trajectory_by_day_week()`      |Generate trajectory view by day week provided by user.       |

| `plot_trajectory_by_date()`   | Generate trajectory view by period of time provided by user. |
| `plot_trajectory_by_hour()`      | Generate trajectory view by period of time provided by user.    |
| `plot_stops()`      | Generate points on map that represents stops points with folium.    |

---



`generate_color()`

Generates  a random color

> Returns

-  Random HEX color

---

`rgb(rgb_colors)`

Return a tuple of integers, as used in AWT/Java plots.
 
> Parameters
   
- rgb_colors (list)
Represents a list with three positions that correspond to the percentage red, green and blue colors.
   
> Returns
   
  - tuple
Represents a tuple of integers that correspond the colors values.
    
> Examples

```python
>>> from pymove.visualization.visualization import rgb
>>> rgb([0.6,0.2,0.2]) 
 (51, 51, 153)
```

---

`hex_rgb(rgb_colors)`

Return a hex string, as used in Tk plots.

> Parameters

- rgb_colors : list
        Represents a list with three positions that correspond to the percentage red, green and
        blue colors.
    Returns
    -------
    String
        Represents a color in hexadecimal format.
    Examples
    --------
    >>> from pymove.visualization.visualization import hex_rgb
    >>> hex_rgb([0.6,0.2,0.2])
    '#333399'
    """
---

 cmap_hex_color(cmap, i):
"""
    Convert a Colormap to hex color.
    Parameters
    ----------
    cmap : matplotlib.colors.ListedColormap
        Represents the Colormap.
    i : int
        List color index.
    Returns
    -------
    String
        Represents corresponding hex string.
    """
---
add_map_legend(m, title, items):
???

---
 save_map(
    move_data, filename, tiles="OpenStreetMap", label_id=TRAJ_ID, cmap="tab20"
):
    """
    Save a visualization in a map in a new file.
    Parameters
    ----------
    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    filename : String
        Represents the filename.
    tiles : String
        Represents the type of tile that will be used on the map.
    label_id : String
        Represents column name of trajectory id.
    cmap: String
        Represents the Colormap.
    Returns
    -------
    """
---
save_wkt(move_data, filename, label_id=TRAJ_ID):
    """
    Save a visualization in a map in a new file .wkt.
    Parameters
    ----------
    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    filename : String
        Represents the filename.
    label_id : String
        Represents column name of trajectory id.
    Returns
    -------
    """
	
---

show_object_id_by_date(
    move_data,
    create_features=True,
    kind=["bar", "bar", "line", "line"],
    figsize=(21, 9),
    return_fig=True,
    save_fig=True,
    name="shot_points_by_date.png",
):
    """
    Generates four visualizations based on datetime feature:
        - Bar chart trajectories by day periods
        - Bar chart trajectories day of the week
        - Line chart trajectory by date
        - Line chart of trajectory byhours of the day.
    Parameters
    ----------
    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    create_features : bool, optional, default True.
        Represents whether or not to delete features created for viewing.
    kind: list or None
        Determines the kinds of each plot
    figsize : tuple, optional, default (21,9).
        Represents dimensions of figure.
    return_fig : bool, optional, default True.
        Represents whether or not to save the generated picture.
    save_fig : bool, optional, default True.
        Represents whether or not to save the generated picture.
    name : String, optional, default 'shot_points_by_date.png'.
        Represents name of a file.
    Returns
    -------
    fig : matplotlib.pyplot.figure or None
        The generated picture.
    References
    ----------
    https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.plot.html
    """
	
---
show_lat_lon_gps(
    move_data,
    kind="scatter",
    figsize=(21, 9),
    plot_start_and_end=True,
    return_fig=True,
    save_fig=False,
    name="show_gps_points.png",
):
    """
    Generate a visualization with points [lat, lon] of dataset.
    Parameters
    ----------
    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    kind : String, optional, default 'scatter'.
        Represents chart type.
    figsize : tuple, optional, default (21,9).
        Represents dimensions of figure.
    plot_start_and_end: boolean
        Whether to highlight the start and end of the trajectory
    return_fig : bool, optional, default True.
        Represents whether or not to save the generated picture.
    save_fig : bool, optional, default True.
        Represents whether or not to save the generated picture.
    name : String, optional, default 'show_gps_points.png'.
        Represents name of a file.
    Returns
    -------
    fig : matplotlib.pyplot.figure or None
        The generated picture.
		
---
create_base_map(default_location, tile=TILES[0], default_zoom_start=12):
    """
    Generate a folium map.
    Parameters
    ----------
    default_location : tuple.
        Represents coordinates lat, lon which will be the center of the map.
    default_zoom_start : int, optional, default 12.
        Represents the zoom which will be the center of the map.
    tile : String, optional, default 'OpenStreetMap'.
        Represents the map's tiles.
    Returns
    -------
    base_map : folium.folium.Map.
        Represents a folium map.
    """
	
---
 heatmap(
    move_data,
    n_rows=None,
    lat_origin=None,
    lon_origin=None,
    zoom_start=12,
    radius=8,
    max_zoom=13,
    base_map=None,
    tile=TILES[0],
    save_as_html=False,
    filename="heatmap.html",
):
    """
    Generate visualization of Heat Map using folium plugin.
    Parameters
    ----------
    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    n_rows : int, optional, default None.
        Represents number of data rows that are will plot.
    lat_origin : float, optional, default None.
        Represents the latitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    lon_origin : float, optional, default None.
        Represents the longitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    zoom_start : int, optional, default 12.
        Initial zoom level for the map
    radius : float, optional, default 8.
        Radius of each “point” of the heatmap.
    max_zoom : int, optional, default 13.
        Zoom level where the points reach maximum intensity (as intensity
        scales with zoom), equals maxZoom of the map by default.
    base_map : folium.folium.Map, optional, default None.
        Represents the folium map. If not informed, a new map is generated
        using the function create_base_map(), with the lat_origin, lon_origin
        and zoom_start.
    tile : String, optional, default 'OpenStreetMap'.
        Represents the map's tiles.
    save_as_html : bool, optional, default False.
        Represents if want save this visualization in a new file .html.
    filename : String, optional, default 'heatmap.html'.
        Represents the file name of new file .html.
    Returns
    -------
    base_map : folium.folium.Map.
        Represents a folium map with visualization.
    """
	
---
cluster(
    move_data,
    n_rows=None,
    lat_origin=None,
    lon_origin=None,
    zoom_start=12,
    base_map=None,
    tile=TILES[0],
    save_as_html=False,
    filename="cluster.html",
):
    """
    Generate visualization of Marker Cluster using folium plugin.
    Parameters
    ----------
    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    n_rows : int, optional, default None.
        Represents number of data rows that are will plot.
    lat_origin : float, optional, default None.
        Represents the latitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    lon_origin : float, optional, default None.
        Represents the longitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    zoom_start : int, optional, default 12.
        Initial zoom level for the map
    base_map : folium.folium.Map, optional, default None.
        Represents the folium map. If not informed, a new map is generated
        using the function create_base_map(), with the lat_origin, lon_origin
        and zoom_start.
    tile : String, optional, default 'OpenStreetMap'.
        Represents the map's tiles.
    save_as_html : bool, optional, default False.
        Represents if want save this visualization in a new file .html.
    filename : String, optional, default 'cluster.html'.
        Represents the file name of new file .html.
    Returns
    -------
    base_map : folium.folium.Map.
        Represents a folium map with visualization.
    """
---
faster_cluster(
    move_data,
    n_rows=None,
    lat_origin=None,
    lon_origin=None,
    zoom_start=12,
    base_map=None,
    tile=TILES[0],
    save_as_html=False,
    filename="faster_cluster.html",
):
    """
    Generate visualization of Faster Cluster using folium plugin.
    Parameters
    ----------
    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    n_rows : int, optional, default None.
        Represents number of data rows that are will plot.
    lat_origin : float, optional, default None.
        Represents the latitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    lon_origin : float, optional, default None.
        Represents the longitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    zoom_start : int, optional, default 12.
        Initial zoom level for the map
    base_map : folium.folium.Map, optional, default None.
        Represents the folium map. If not informed, a new map is generated
        using the function create_base_map(), with the lat_origin, lon_origin
        and zoom_start.
    tile : String, optional, default 'OpenStreetMap'.
        Represents the map's tiles.
    save_as_html : bool, optional, default False.
        Represents if want save this visualization in a new file .html.
    filename : String, optional, default 'faster_cluster.html'.
        Represents the file name of new file .html.
    Returns
    -------
---

plot_markers(
    move_data,
    n_rows=None,
    lat_origin=None,
    lon_origin=None,
    zoom_start=12,
    base_map=None,
    tile=TILES[0],
    save_as_html=False,
    filename="plot_markers.html",
):
    """
    Plot markers of Folium on map.

> Parameters

- move_data : pymove.core.MoveDataFrameAbstract subclass.
Input trajectory data.
    
- n_rows : int, optional, default None.
Represents number of data rows that are will plot.
    
- lat_origin : float, optional, default None.
Represents the latitude which will be the center of the map.
If not entered, the first data from the dataset is used.

- lon_origin : float, optional, default None.
Represents the longitude which will be the center of the map.
If not entered, the first data from the dataset is used.
    
- zoom_start : int, optional, default 12.
Initial zoom level for the map

- base_map : folium.folium.Map, optional, default None.
Represents the folium map. If not informed, a new map is generated
using the function create_base_map(), with the lat_origin,
lon_origin and zoom_start.
    
- tile : String, optional, default 'OpenStreetMap'.
Represents the map's tiles.

- save_as_html : bool, optional, default False.
Represents if want save this visualization in a new file .html.

- filename : String, optional, default 'plot_trejectory_with_folium.html'.
Represents the file name of new file .html.
    
> Returns

- base_map : folium.folium.Map.
Represents a folium map with visualization.
	
---

`plot_trajectories_with_folium(move_data, n_rows=None, lat_origin=None, lon_origin=None, zoom_start=12, base_map=None, tile=TILES[0], save_as_html=False, color="black", filename="plot_trajectories_with_folium.html")`

Generate visualization of all trajectories with folium.

> Parameters

    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    n_rows : int, optional, default None.
        Represents number of data rows that are will plot.
    lat_origin : float, optional, default None.
        Represents the latitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    lon_origin : float, optional, default None.
        Represents the longitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    zoom_start : int, optional, default 12.
        Initial zoom level for the map
    base_map : folium.folium.Map, optional, default None.
        Represents the folium map. If not informed, a new map is generated
        using the function create_base_map(), with the lat_origin, lon_origin
         and zoom_start.
    tile : String, optional, default 'OpenStreetMap'.
        Represents the map's tiles.
    save_as_html : bool, optional, default False.
        Represents if want save this visualization in a new file .html.
    color : String, optional, default 'black'.
        Represents line's color of visualization.
    filename : String, optional, default 'plot_trajectory_with_folium.html'.
        Represents the file name of new file .html.
    Returns
    -------
    base_map : folium.folium.Map.
        Represents a folium map with visualization.
    """
	
---
 plot_trajectory_by_id_with_folium(
    move_data,
    id_,
    n_rows=None,
    lat_origin=None,
    lon_origin=None,
    zoom_start=12,
    base_map=None,
    tile=TILES[0],
    save_as_html=False,
    color="black",
    filename="plot_trajectory_by_id_with_folium.html",
):
    """
    Generate visualization of trajectory with the id provided by user.
    Parameters
    ----------
    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    id_: int
        Represents trajectory ID.
    n_rows : int, optional, default None.
        Represents number of data rows that are will plot.
    lat_origin : float, optional, default None.
        Represents the latitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    lon_origin : float, optional, default None.
        Represents the longitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    zoom_start : int, optional, default 12.
        Initial zoom level for the map
    base_map : folium.folium.Map, optional, default None.
        Represents the folium map. If not informed, a new map is
        generated using the function create_base_map(), with the
        lat_origin, lon_origin and zoom_start.
    tile : String, optional, default 'OpenStreetMap'.
        Represents the map's tiles.
    save_as_html : bool, optional, default False.
        Represents if want save this visualization in a new file .html.
    color : String, optional, default 'black'.
        Represents line's color of visualization.
    filename : String, optional, default 'plot_trajectory_by_id_with_folium.html'.
        Represents the file name of new file .html.
    Returns
    -------
    base_map : folium.folium.Map.
        Represents a folium map with visualization.
    Raises
    ------
        IndexError if there is no user with the id passed
    """
	
---

 plot_trajectory_by_period(
    move_data,
    period,
    id_=None,
    legend=True,
    n_rows=None,
    lat_origin=None,
    lon_origin=None,
    zoom_start=12,
    base_map=None,
    tile=TILES[0],
    save_as_html=False,
    color="black",
    filename="plot_trajectory_by_period_with_folium.html",
):
    """
    Generate trajectory view by period of day provided by user.
    Parameters
    ----------
    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    period: String
        Represents period of day.
    id_: int or None
        If int, plots trajectory of the user, else plot for all users
    legend: boolean
        Whether to add a legend to the map
    n_rows : int, optional, default None.
        Represents number of data rows that are will plot.
    lat_origin : float, optional, default None.
        Represents the latitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    lon_origin : float, optional, default None.
        Represents the longitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    zoom_start : int, optional, default 12.
        Initial zoom level for the map
    base_map : folium.folium.Map, optional, default None.
        Represents the folium map. If not informed, a new map is generated
        using the function create_base_map(), with the lat_origin,
        lon_origin and zoom_start.
    tile : String, optional, default 'OpenStreetMap'.
        Represents the map's tiles.
    save_as_html : bool, optional, default False.
        Represents if want save this visualization in a new file .html.
    color : String or List, optional, default 'black'.
        Represents line's color of visualization.
        Pass a list if ploting for many users. Else colors will be chosen at random
    filename : String, optional, default 'plot_trajectory_by_period.html'.
        Represents the file name of new file .html.
    Returns
    -------
    base_map : folium.folium.Map.
        Represents a folium map with visualization.
    Raises
    ------
        KeyError period not found in dataframe
        IndexError if there is no user with the id passed
    """
---

 plot_trajectory_by_day_week(
    move_data,
    day_week,
    id_=None,
    legend=True,
    n_rows=None,
    lat_origin=None,
    lon_origin=None,
    zoom_start=12,
    base_map=None,
    tile=TILES[0],
    save_as_html=False,
    color="black",
    filename="plot_trajectory_by_day_week.html",
):
    """
    Generate trajectory view by day week provided by user.
    Parameters
    ----------
    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    day_week: String
        Represents day week.
    id_: int or None
        If int, plots trajectory of the user, else plot for all users
    legend: boolean
        Whether to add a legend to the map
    n_rows : int, optional, default None.
        Represents number of data rows that are will plot.
    lat_origin : float, optional, default None.
        Represents the latitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    lon_origin : float, optional, default None.
        Represents the longitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    zoom_start : int, optional, default 12.
        Initial zoom level for the map
    base_map : folium.folium.Map, optional, default None.
        Represents the folium map. If not informed, a new map is generated
        using the function create_base_map(), with the lat_origin,
        lon_origin and zoom_start.
    tile : String, optional, default 'OpenStreetMap'.
        Represents the map's tiles.
    save_as_html : bool, optional, default False.
        Represents if want save this visualization in a new file .html.
    color : String or List, optional, default 'black'.
        Represents line's color of visualization.
        Pass a list if ploting for many users. Else colors will be chosen at random
    filename : String, optional, default 'plot_trajectory_by_day_week.html'.
        Represents the file name of new file .html.
    Returns
    -------
    base_map : folium.folium.Map.
        Represents a folium map with visualization.
    Raises
    ------
        KeyError day_week not found in dataframe
        IndexError if there is no user with the id passed
    """
---

plot_trajectory_by_date(
    move_data,
    start_date,
    end_date,
    id_=None,
    legend=True,
    n_rows=None,
    lat_origin=None,
    lon_origin=None,
    zoom_start=12,
    base_map=None,
    tile=TILES[0],
    save_as_html=False,
    color="black",
    filename="plot_trajectory_by_date.html",
):
    """
    Generate trajectory view by period of time provided by user.
    Parameters
    ----------
    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    start_date : String
        Represents start date of time period.
    end_date : String
        Represents end date of time period.
    id_: int or None
        If int, plots trajectory of the user, else plot for all users
    legend: boolean
        Whether to add a legend to the map
    n_rows : int, optional, default None.
        Represents number of data rows that are will plot.
    lat_origin : float, optional, default None.
        Represents the latitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    lon_origin : float, optional, default None.
        Represents the longitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    zoom_start : int, optional, default 12.
        Initial zoom level for the map
    base_map : folium.folium.Map, optional, default None.
        Represents the folium map. If not informed, a new map is generated
        using the function create_base_map(), with the lat_origin,
        lon_origin and zoom_start.
    tile : String, optional, default 'OpenStreetMap'.
        Represents the map's tiles.
    save_as_html : bool, optional, default False.
        Represents if want save this visualization in a new file .html.
    color : String or List, optional, default 'black'.
        Represents line's color of visualization.
        Pass a list if ploting for many users. Else colors will be chosen at random
    filename : String, optional, default 'plot_trejectory_with_folium.html'.
        Represents the file name of new file .html.
    Returns
    -------
    base_map : folium.folium.Map.
        Represents a folium map with visualization.
    Raises
    ------
        KeyError start or end date range not found in dataframe
        IndexError if there is no user with the id passed
    """
	
---

plot_trajectory_by_hour(
    move_data,
    start_hour,
    end_hour,
    id_=None,
    legend=True,
    n_rows=None,
    lat_origin=None,
    lon_origin=None,
    zoom_start=12,
    base_map=None,
    tile=TILES[0],
    save_as_html=False,
    color="black",
    filename="plot_trajectory_by_hour.html",
):
    """
    Generate trajectory view by period of time provided by user.
    Parameters
    ----------
    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    start_hour : int
        Represents start hour of time period.
    end_hour : int
        Represents end hour of time period.
    id_: int or None
        If int, plots trajectory of the user, else plot for all users
    legend: boolean
        Whether to add a legend to the map
    n_rows : int, optional, default None.
        Represents number of data rows that are will plot.
    lat_origin : float, optional, default None.
        Represents the latitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    lon_origin : float, optional, default None.
        Represents the longitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    zoom_start : int, optional, default 12.
        Initial zoom level for the map
    base_map : folium.folium.Map, optional, default None.
        Represents the folium map. If not informed, a new map is generated
        using the function create_base_map(), with the lat_origin,
        lon_origin and zoom_start.
    tile : String, optional, default 'OpenStreetMap'.
        Represents the map's tiles.
    save_as_html : bool, optional, default False.
        Represents if want save this visualization in a new file .html.
    color : String or List, optional, default 'black'.
        Represents line's color of visualization.
        Pass a list if ploting for many users. Else colors will be chosen at random
    filename : String, optional, default 'plot_trajectory_by_hour.html'.
        Represents the file name of new file .html.
    Returns
    -------
    base_map : folium.folium.Map.
        Represents a folium map with visualization.
    Raises
    ------
        KeyError if start to end hour range not found in dataframe
        IndexError if there is no user with the id passed
    """
	
---

 plot_stops(
    move_data,
    radius=0,
    weight=3,
    id_=None,
    legend=True,
    n_rows=None,
    lat_origin=None,
    lon_origin=None,
    zoom_start=12,
    base_map=None,
    tile=TILES[0],
    save_as_html=False,
    color="black",
    filename="plot_stops.html",
):
    """
    Generate points on map that represents stops points with folium.
    Parameters
    ----------
    move_data : pymove.core.MoveDataFrameAbstract subclass.
        Input trajectory data.
    radius :  Double, optional(900 by default)
        The radius value is used to determine if a segment is a stop.
        If the value of the point in target_label is greater than
        radius, the segment is a stop, otherwise it's a move.
    weight: int or None
        Stroke width in pixels
    id_: int or None
        If int, plots trajectory of the user, else plot for all users
    legend: boolean
        Whether to add a legend to the map
    n_rows : int, optional, default None.
        Represents number of data rows that are will plot.
    lat_origin : float, optional, default None.
        Represents the latitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    lon_origin : float, optional, default None.
        Represents the longitude which will be the center of the map.
        If not entered, the first data from the dataset is used.
    zoom_start : int, optional, default 12.
        Initial zoom level for the map
    base_map : folium.folium.Map, optional, default None.
        Represents the folium map. If not informed, a new map is generated
        using the function create_base_map(), with the lat_origin,
        lon_origin and zoom_start.
    tile : String, optional, default 'OpenStreetMap'.
        Represents the map's tiles.
    save_as_html : bool, optional, default False.
        Represents if want save this visualization in a new file .html.
    color : String or List, optional, default 'black'.
        Represents line's color of visualization.
        Pass a list if ploting for many users. Else colors will be chosen at random
    filename : String, optional, default 'plot_stops.html'.
        Represents the file name of new file .html.
    Returns
    -------
    base_map : folium.folium.Map.
        Represents a folium map with visualization.
    Raises
        ------
        KeyError if no STOPs found
        IndexError if there is no user with the id passed
    """
	
---




---





