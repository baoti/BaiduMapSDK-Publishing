百度地图Android SDK自v2.3.0起，采用可定制的形式为您提供开发包，当前开发包包含如下功能:
基础地图：地图显示、操作和各种覆盖物图层：
检索功能：POI检索、地理编码、路径规划等；
LBS云检索：基于LBS云的周边、城市内、区域、详情检索；
计算工具：调启百度地图客户端导航、调启Web App导航、计算距离等；

------------------------------------------------------------------------------------------------
Android SDK v3.4.0是适用于Android系统移动设备的矢量地图开发包
------------------------------------------------------------------------------------------------
注意：为了给用户提供更安全的服务，Android SDK自v2.1.3版本开始采用了全新的Key验证体系。因此，当您选择使用v2.1.3及之后版本的SDK时，需要到新的Key申请页面进行全新Key的申请，申请及配置流程请参考开发指南的对应章节。（选择使用v2.1.2及之前版本SDK的开发者，申请密钥（Key） 的方式不变）
------------------------------------------------------------------------------------------------
地图SDK功能介绍（全功能开发包）：

地图：
    提供地图（2D、3D）的展示和缩放、平移、旋转、改变视角等地图操作；
POI检索：
    可根据关键字，对POI数据进行周边、区域和城市内三种检索；
地理编码：
    提供地理坐标和地址之间相互转换的能力；
线路规划：
    支持公交信息查询、公交换乘查询、驾车线路规划和步行路径检索；
覆盖物：
    提供多种地图覆盖物（自定义标注、几何图形、文字绘制、地形图图层、热力图图层等），满足开发者的各种需求；
定位：
    采用多种定位模式，使用定位SDK获取位置信息，使用地图SDK我的位置图层进行位置展示；
离线地图：
    支持使用离线地图，节省用户流量，同时为用户带来更好的地图体验；
导航：
    支持调启百度地图导航和Web导航来满足用户对导航功能的需求；
LBS云检索：
    支持用户检索存储在LBS云内的自有POI数据，并展示；
特色功能：
    提供短串分享、Place详情检索、热力图、调启百度地图等特色功能，帮助开发者搭建功能更加强大的应用；

------------------------------------------------------------------------------------------------
较之v3.3.0，升级功能：

【 新 增 】
基础地图
    1. 新增地图缩放等级到20级（10米）；
    2. 新增获取当前地图显示范围的方法：
	MapStatus类新增LatLngBounds bound;属性
检索功能
    1. 开放驾车线路规划，返回多条线路的能力：
	DrivingRouteResult中getRouteLines()方法将最多返回3条路线
    2. 驾车线路规划结果中，新增路况信息字段：
	DrivingRouteLine.DrivingStep类中新增路段路况属性，通过getTrafficList()获得
    3. POI城市检索中，当前城市检索不到结果时，新增返回建议检索城市列表：
	onGetPoiResult监听中当result.error == SearchResult.ERRORNO.AMBIGUOUS_KEYWORD，需通过PoiResult类的getSuggestCityList方法获取城市列表处理
计算工具
    1. 新增调启百度地图客户端功能；
	PoiParaOption为poi检索调起的参数结构
        BaiduMapPoiSearch为调起百度地图APP或webApp的管理类，包含setSupportWebPoi、openBaiduMapPoiDetialsPage、openBaiduMapPoiNearbySearch、finish方法
        RouteParaOption为路线检索调起的参数结构
        BaiduMapRoutePlan为调起百度地图APP或webApp的管理类，包含setSupportWebRoute、openBaiduMapWalkingRout、openBaiduMapTransitRoute、openBaiduMapDrivingRoute、finish方法
    2. 新增收藏夹功能；
	FavoritePoiInfo类为收藏点结构
	FavoriteManager为收藏夹管理类，是单例模式，包含add、getFavPoi、getAllFavPois、deleteFavPoi、clearAllFavPoi、updateFavPoi方法
【 优 化 】
    1. 减少首次启动SDK时的数据流量；
    2. setOnMarkerClickListener可接收多个监听对象，同时提供removeMarkerClickListener方法来移除监听对象；
【 修 复 】
    1. 修复Maker属性更新方法（例如setToTop），导致Marker不显示的bug；