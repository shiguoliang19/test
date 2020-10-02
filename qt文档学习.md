



## QStandardItemModel


```c++
//构造，析构
QStandardItemModel(QObject * parent = 0)；
QStandardItemModel(int rows, int columns, QObject * parent = 0)；
~QStandardItemModel()；
//索引与项的转换
QModelIndex	indexFromItem(const QStandardItem * item) const；
QStandardItem *	itemFromIndex(const QModelIndex & index) const；
//设置行，列数量
void setColumnCount(int columns)；
void setRowCount(int rows);
//设置，获取排序角色
void setSortRole(int role)；
int	sortRole() const;
//设置，获取项原型  
const QStandardItem* itemPrototype() const；
void setItemPrototype(const QStandardItem* item);
//设置项角色名称
void setItemRoleNames(const QHash<int, QByteArray> & roleNames)；
```

```c++
//设置水平，垂直头部项
void setVerticalHeaderItem(int row, QStandardItem * item)；
void setHorizontalHeaderItem(int column, QStandardItem * item)；
//拿出水平，垂直头部项
QStandardItem *	takeHorizontalHeaderItem(int column)；
QStandardItem *	takeVerticalHeaderItem(int row)；
//获取水平，垂直头部项
QStandardItem *	verticalHeaderItem(int row) const；
QStandardItem *	horizontalHeaderItem(int column) const；
//设置水平，垂直标签
void setHorizontalHeaderLabels(const QStringList & labels)；
void setVerticalHeaderLabels(const QStringList & labels)；
```



```c++
//添加行，列
void appendColumn(const QList<QStandardItem *> & items)；
void appendRow(const QList<QStandardItem *> & items)；
void appendRow(QStandardItem * item)；
//插入行，列
void insertColumn(int column, const QList<QStandardItem *> & items)；
bool insertColumn(int column, const QModelIndex & parent = QModelIndex())；
void insertRow(int row, const QList<QStandardItem *> & items)；
bool insertRow(int row, const QModelIndex & parent = QModelIndex())；
void insertRow(int row, QStandardItem * item)；
//拿出行，列
QList<QStandardItem *>	takeColumn(int column)；
QStandardItem *	takeItem(int row, int column = 0)；
QList<QStandardItem *>	takeRow(int row)；
//设置行，列
QStandardItem *	item(int row, int column = 0) const；
void setItem(int row, int column, QStandardItem * item)；
void setItem(int row, QStandardItem * item)；
//查找项
QList<QStandardItem *>	findItems(const QString & text, Qt::MatchFlags flags = Qt::MatchExactly, int column = 0) const；
//清理
void clear()；
//获取根索引
QStandardItem *	invisibleRootItem() const；
```

## QAbstractItemModel

```c++
//构造，析构
QAbstractItemModel(QObject * parent = 0)；
virtual	~QAbstractItemModel()；
//可以取得数据更多数据
virtual bool canFetchMore(const QModelIndex & parent) const；
virtual void fetchMore(const QModelIndex & parent)；
//索引标志
virtual Qt::ItemFlags flags(const QModelIndex & index) const；
//项角色名称
virtual QHash<int, QByteArray>	roleNames() const；
//排序
virtual void sort(int column, Qt::SortOrder order = Qt::AscendingOrder)；
//索引位置
virtual QSize span(const QModelIndex & index) const；
```



```c++
//可以放下的mime类型
virtual bool canDropMimeData(const QMimeData * data, Qt::DropAction action, int row, int column, const QModelIndex & parent) const；
//放下的mime类型
virtual bool dropMimeData(const QMimeData * data, Qt::DropAction action, int row, int column, const QModelIndex & parent)；
//mime类型数据
virtual QMimeData *	mimeData(const QModelIndexList & indexes) const；
//mime类型
virtual QStringList	mimeTypes() const；
//支持的拖放动作
virtual Qt::DropActions	supportedDragActions() const；
virtual Qt::DropActions	supportedDropActions() const；
```



```c++
//设置，获取头部数据
virtual QVariant headerData(int section, Qt::Orientation orientation, int role = Qt::DisplayRole) const;
virtual bool setHeaderData(int section, Qt::Orientation orientation, const QVariant & value, int role = Qt::EditRole);
//获取父索引
virtual QModelIndex	parent(const QModelIndex & index) const = 0;
//是否有孩子
virtual bool hasChildren(const QModelIndex & parent = QModelIndex()) const;
bool hasIndex(int row, int column, const QModelIndex & parent = QModelIndex()) const;
//伙伴
virtual QModelIndex	buddy(const QModelIndex & index) const;
//兄弟
virtual QModelIndex	sibling(int row, int column, const QModelIndex & index) const;
```



```c++
//插入行，列
bool insertColumn(int column, const QModelIndex & parent = QModelIndex())；
virtual bool insertColumns(int column, int count, const QModelIndex & parent = QModelIndex())；
bool insertRow(int row, const QModelIndex & parent = QModelIndex())；
virtual bool insertRows(int row, int count, const QModelIndex & parent = QModelIndex())；
 //移动行，列
bool moveColumn(const QModelIndex & sourceParent, int sourceColumn, const QModelIndex & destinationParent, int destinationChild)；
virtual bool moveColumns(const QModelIndex & sourceParent, int sourceColumn, int count, const QModelIndex & destinationParent, int destinationChild)；
bool moveRow(const QModelIndex & sourceParent, int sourceRow, const QModelIndex & destinationParent, int destinationChild)；
virtual bool moveRows(const QModelIndex & sourceParent, int sourceRow, int count, const QModelIndex & destinationParent, int destinationChild)；
//移除行，列
bool removeColumn(int column, const QModelIndex & parent = QModelIndex())
virtual bool removeColumns(int column, int count, const QModelIndex & parent = QModelIndex())
bool removeRow(int row, const QModelIndex & parent = QModelIndex())
virtual bool removeRows(int row, int count, const QModelIndex & parent = QModelIndex())
//获取行，列数量
virtual int	rowCount(const QModelIndex & parent = QModelIndex()) const = 0；
virtual int	columnCount(const QModelIndex & parent = QModelIndex()) const = 0；  
 //获取项
virtual QModelIndex	index(int row, int column, const QModelIndex & parent = QModelIndex()) const = 0；
//获取，设置项数据
virtual QVariant data(const QModelIndex & index, int role = Qt::DisplayRole) const = 0；
virtual bool setData(const QModelIndex & index, const QVariant & value, int role = Qt::EditRole)；
//获取，设置项数据容器
virtual QMap<int, QVariant>	itemData(const QModelIndex & index) const；
virtual bool setItemData(const QModelIndex & index, const QMap<int, QVariant> & roles)；
//匹配项
virtual QModelIndexList	match(const QModelIndex & start, int role, const QVariant & value, int hits = 1, Qt::MatchFlags flags = Qt::MatchFlags( Qt::MatchStartsWith | Qt::MatchWrap )) const；
```

## QAbstractButton

```c++
//构造，析构
QAbstractButton(QWidget * parent = 0);
~QAbstractButton();
//自动互斥
bool autoExclusive() const;
void setAutoExclusive(bool);
//自动重复
bool autoRepeat() const;
void setAutoRepeat(bool);
//自动重复
int	autoRepeatDelay() const;
void setAutoRepeatDelay(int);
//自动重复时间间隔
int	autoRepeatInterval() const;
void setAutoRepeatInterval(int);
//是否是可检查的
bool isCheckable() const;
void setCheckable(bool);
//按下按钮
bool isDown() const;
void setDown(bool);
//文字
void setText(const QString & text);
QString	text() const;
//图标
void setIcon(const QIcon & icon);
QIcon icon() const;
//图标大小
QSize iconSize() const;
void setIconSize(const QSize & size)；
//快捷键
void setShortcut(const QKeySequence & key);
QKeySequence shortcut() const;
//按下状态
void setChecked(bool)；
bool isChecked() const;
//按钮所属组
QButtonGroup* group() const;
//动画点击
void animateClick(int msec = 100)；
//点击
void click()；
//触发
void toggle()；
```

## QPushButton

```c++
//构造，析构
QPushButton(QWidget * parent = 0);
QPushButton(const QString & text, QWidget * parent = 0);
QPushButton(const QIcon & icon, const QString & text, QWidget * parent = 0);
~QPushButton();
//自动默认
bool autoDefault() const;
void setAutoDefault(bool);
//设置默认
void setDefault(bool);
bool isDefault() const;
//是否是单调的
bool isFlat() const;
void setFlat(bool);
//设置菜单
QMenu *	menu() const;
void setMenu(QMenu * menu);
```

## QToolButton

```c++
//构造，析构
QToolButton(QWidget * parent = 0);
~QToolButton();
//按钮样式
Qt::ToolButtonStyle	toolButtonStyle() const;
void setToolButtonStyle(Qt::ToolButtonStyle style);
//按钮菜单卡
void setMenu(QMenu * menu);
QMenu* menu() const;
//按钮菜单弹出方式
void setPopupMode(ToolButtonPopupMode mode);
ToolButtonPopupMode	popupMode() const;
//按钮箭头类型
void setArrowType(Qt::ArrowType type);
Qt::ArrowType arrowType() const;
//按钮升起
bool autoRaise() const;
void setAutoRaise(bool enable);
//按钮默认动作
QAction* defaultAction() const;
void setDefaultAction(QAction * action);
```

## QRadioButton

```c++
//构造，析构
QRadioButton(QWidget * parent = 0)
QRadioButton(const QString & text, QWidget * parent = 0)
~QRadioButton()
```

备注：默认是检查的，但自动互斥。

## QCheckBox

```c++
//构造，析构
QCheckBox(QWidget * parent = 0);
QCheckBox(const QString & text, QWidget * parent = 0);
~QCheckBox();
//设置检查状态
void setCheckState(Qt::CheckState state);
Qt::CheckState checkState() const;
//设置是否三态
void setTristate(bool y = true);
bool isTristate() const;
```

备注：默认是检查的，为二态，不自动互斥。

## QSplitter

```c++
//构造，析构
QSplitter(QWidget * parent = 0);
QSplitter(Qt::Orientation orientation, QWidget * parent = 0);
~QSplitter();
//添加，插入窗口
void addWidget(QWidget * widget);
void insertWidget(int index, QWidget * widget);
//获取窗口
QWidget* widget(int index) const;
//获取窗口索引
int	indexOf(QWidget * widget) const;
//获取窗口位置
void getRange(int index, int * min, int * max) const;
//数量
int	count() const;
//设置窗口拉伸因子
void setStretchFactor(int index, int stretch);
//分割器方向
Qt::Orientation	orientation() const;
void setOrientation(Qt::Orientation);
//处理者宽度
int	handleWidth() const;
void setHandleWidth(int);
//获取取处理者
QSplitterHandle * handle(int index) const;
//窗口初聚始大小
void setSizes(const QList<int> & list);
QList<int> sizes() const;
//保存，恢复
bool restoreState(const QByteArray & state);
QByteArray saveState() const;
//可折叠
void setChildrenCollapsible(bool);
bool childrenCollapsible() const;
void setCollapsible(int index, bool collapse);
bool isCollapsible(int index) const;
//不透明调整
void setOpaqueResize(bool opaque = true);
bool opaqueResize() const;
//更新
void refresh();
```

## QAbstractScrollArea

```c++
//构造，析构
QAbstractScrollArea(QWidget * parent = 0);
~QAbstractScrollArea();
//设置，获取水平，垂直滚动条
void setVerticalScrollBar(QScrollBar * scrollBar);
void setHorizontalScrollBar(QScrollBar * scrollBar);
QScrollBar * horizontalScrollBar() const;
QScrollBar * verticalScrollBar() const;
//设置，获取水平，垂直滚动条策略
Qt::ScrollBarPolicy horizontalScrollBarPolicy() const;
Qt::ScrollBarPolicy verticalScrollBarPolicy() const;
void setHorizontalScrollBarPolicy(Qt::ScrollBarPolicy);
void setVerticalScrollBarPolicy(Qt::ScrollBarPolicy);
//设置滚动窗口加入大小策略
void setSizeAdjustPolicy(SizeAdjustPolicy policy);
SizeAdjustPolicy sizeAdjustPolicy() const;
//设置角落小部件
void setCornerWidget(QWidget * widget);
QWidget * cornerWidget() const;
//添加到滚动条窗口左右，上下位置窗口
void addScrollBarWidget(QWidget * widget, Qt::Alignment alignment);
QWidgetList	scrollBarWidgets(Qt::Alignment alignment);
//设置视口
QWidget * viewport() const;
void setViewport(QWidget * widget);
virtual void setupViewport(QWidget * viewport);
//最大视口大小
QSize	maximumViewportSize() const;
```

## QScrollArea

```c++
//构造，析构
QScrollArea(QWidget * parent = 0);
~QScrollArea();
//设置，拿出，获取窗口
void setWidget(QWidget * widget);
QWidget * widget() const;
QWidget * takeWidget();
//设置对齐方式
void setAlignment(Qt::Alignment);
Qt::Alignment alignment() const;
//设置小部件可以调整
void setWidgetResizable(bool resizable);
bool widgetResizable() const;
//确保可见
void ensureVisible(int x, int y, int xmargin = 50, int ymargin = 50);
void ensureWidgetVisible(QWidget * childWidget, int xmargin = 50, int ymargin = 50);
```

## QLayout

```c++
QLayout(QWidget * parent);
QLayout();
//添加项
virtual void addItem(QLayoutItem * item) = 0;
void addWidget(QWidget * w);
//移除项
void removeItem(QLayoutItem * item);
void removeWidget(QWidget * widget);
//索引值
virtual int	indexOf(QWidget * widget) const;
//获取项
virtual QLayoutItem * itemAt(int index) const = 0;
//替换窗口
QLayoutItem * replaceWidget(QWidget * from, QWidget * to, Qt::FindChildOptions options = Qt::FindChildrenRecursively);
//拿出窗口
virtual QLayoutItem * takeAt(int index) = 0;
//设置对齐方式
bool setAlignment(QWidget * w, Qt::Alignment alignment);
void setAlignment(Qt::Alignment alignment);
bool setAlignment(QLayout * l, Qt::Alignment alignment);
//设置菜单栏
void setMenuBar(QWidget * widget);
QWidget * menuBar() const;
//设置边缘
void setContentsMargins(int left, int top, int right, int bottom);
void setContentsMargins(const QMargins & margins);
void getContentsMargins(int * left, int * top, int * right, int * bottom) const;
QMargins contentsMargins() const;
//间隔
void setSpacing(int);
int	spacing() const;
//父窗口
QWidget * parentWidget() const;
//数量
virtual int	count() const = 0;

void setSizeConstraint(SizeConstraint);
SizeConstraint sizeConstraint() const;

QRect contentsRect() const;

void setEnabled(bool enable);
bool isEnabled() const;
bool activate();
void update();
```

## QGroupBox

```c++
//构造，析构
QGroupBox(QWidget * parent = 0);
QGroupBox(const QString & title, QWidget * parent = 0);
~QGroupBox();
//设置对齐方式
void setAlignment(int alignment);
Qt::Alignment alignment() const;
//设置是否可检查的
void setCheckable(bool checkable);
bool isCheckable() const;
//设置检查
void setChecked(bool checked);
bool isChecked() const;
//是否是单调的
bool isFlat() const;
void setFlat(bool flat);
//设置标题
void setTitle(const QString & title);
QString	title() const;
```

## QStackedWidget

```c++
//构造，析构
QStackedWidget(QWidget * parent = 0);
~QStackedWidget();
//添加，获取窗口
int	addWidget(QWidget * widget);
QWidget * widget(int index) const;
//插入，移除窗口
int	insertWidget(int index, QWidget * widget);
void removeWidget(QWidget * widget);
//通过索引设置当前窗口
void setCurrentIndex(int index);
int	currentIndex() const;
//通过窗口指针设置当前窖口
void setCurrentWidget(QWidget * widget);
QWidget * currentWidget() const;
//返加窗口索引
int	indexOf(QWidget * widget) const;
int	count() const;
```

## QTabWidget

```c++
QTabWidget(QWidget * parent = 0);
~QTabWidget();
//设置标签是否可移动
void setMovable(bool movable);
bool isMovable() const;
//设置图标大小
void setIconSize(const QSize & size);
QSize iconSize() const;
//设置标签文字
void setTabText(int index, const QString & label);
QString	tabText(int index) const;
//设置标签工具提示
void setTabToolTip(int index, const QString & tip);
QString	tabToolTip(int index) const;
//设置标签这是什么
void setTabWhatsThis(int index, const QString & text);
QString	tabWhatsThis(int index) const;
//是否激活标签关闭按钮
void setTabsClosable(bool closeable);
bool tabsClosable() const;
//设置标签图标
void setTabIcon(int index, const QIcon & icon);
QIcon tabIcon(int index) const;
//设置标签位置
void setTabPosition(TabPosition);
TabPosition	tabPosition() const;
//设置标签形状
void setTabShape(TabShape s);
TabShape tabShape() const;
//设置文档模式
void setDocumentMode(bool set);
bool documentMode() const;
//设置省略模式（没有足够空间显示选项栏卡大小时的省略模式）
void setElideMode(Qt::TextElideMode);
Qt::TextElideMode elideMode() const;
//设置是否应用滚动按钮
void setUsesScrollButtons(bool useButtons);
bool usesScrollButtons() const;
//选项栏是否自动隐藏（选项栏数量小于2时有效）
void setTabBarAutoHide(bool enabled);
bool tabBarAutoHide() const;
//设置角落窗口
void setCornerWidget(QWidget * widget, Qt::Corner corner = Qt::TopRightCorner);
QWidget * cornerWidget(Qt::Corner corner = Qt::TopRightCorner) const;
//设置是否激活索引栏
void setTabEnabled(int index, bool enable);
bool isTabEnabled(int index) const;
//标签栏数量
int	count() const;
//返回标签栏
QTabBar * tabBar() const;
```



```c++
//添加标签
int	addTab(QWidget * page, const QString & label);
int	addTab(QWidget * page, const QIcon & icon, const QString & label);
//插入标签
int	insertTab(int index, QWidget * page, const QString & label);
int	insertTab(int index, QWidget * page, const QIcon & icon, const QString & label);
//移除标签
void removeTab(int index);
//当前窗口
QWidget * currentWidget() const;
//当前索引
int	currentIndex() const;
//根据索引获取窗口
QWidget * widget(int index) const;
//获取窗口索引
int	indexOf(QWidget * w) const;
//清理
void clear();
```

## QComboBox

```c++
QComboBox(QWidget * parent = 0);
~QComboBox();
//添加项
void addItem(const QString & text, const QVariant & userData = QVariant());
void addItem(const QIcon & icon, const QString & text, const QVariant & userData = QVariant());
void addItems(const QStringList & texts);
//插入项
void insertItem(int index, const QString & text, const QVariant & userData = QVariant());
void insertItem(int index, const QIcon & icon, const QString & text, const QVariant & userData = QVariant());
void insertItems(int index, const QStringList & list);
//查找数据
int	findData(const QVariant & data, int role = Qt::UserRole, Qt::MatchFlags flags = static_cast<Qt::MatchFlags> ( Qt::MatchExactly | Qt::MatchCaseSensitive )) const;
//查找文本
int	findText(const QString & text, Qt::MatchFlags flags = static_cast<Qt::MatchFlags> ( Qt::MatchExactly | Qt::MatchCaseSensitive )) const;
//移除项
void removeItem(int index);
//清理
void clear();
//设置编辑文字
void setEditText(const QString & text);
void clearEditText();
//当前数据
QVariant currentData(int role = Qt::UserRole) const;
//当前文字
void setCurrentText(const QString & text);
QString	currentText() const;
//当前索引
void setCurrentIndex(int index);
int	currentIndex() const;
//设置项数据
void setItemText(int index, const QString & text);
QString	itemText(int index) const;
//设置项数据
void setItemData(int index, const QVariant & value, int role = Qt::UserRole);
QVariant itemData(int index, int role = Qt::UserRole) const;
//设置项图标
void setItemIcon(int index, const QIcon & icon);
QIcon itemIcon(int index) const;
//设置图标大小
void setIconSize(const QSize & size);
QSize iconSize() const;
//是否有框
void setFrame(bool);
bool hasFrame() const;
//是否可编辑
void setEditable(bool editable);
bool isEditable() const;
//设置自动提示
void setCompleter(QCompleter * completer);
QCompleter * completer() const;
//设置内容过滤
void setValidator(const QValidator * validator);
const QValidator * validator() const;
//设置视图
void setView(QAbstractItemView * itemView);
QAbstractItemView *	view() const;
//设置模型
void setModel(QAbstractItemModel * model);
QAbstractItemModel * model() const;
//设置委托器
void setItemDelegate(QAbstractItemDelegate * delegate);
QAbstractItemDelegate *	itemDelegate() const;、
//设置根索引
void setRootModelIndex(const QModelIndex & index);
QModelIndex	rootModelIndex() const;
//设置模型有效列数
void setModelColumn(int visibleColumn);
int	modelColumn() const;
//行编辑器
void setLineEdit(QLineEdit * edit);
QLineEdit *	lineEdit() const;
//此属性保存组合框中允许的最大项数。
void setMaxCount(int max);
int	maxCount() const;
//此属性保存组合框屏幕上允许的最大大小(以项度量)。
void setMaxVisibleItems(int maxItems);
int	maxVisibleItems() const;
//此属性保存描述当内容更改时combobox的大小如何更改的策略。
void setSizeAdjustPolicy(SizeAdjustPolicy policy);
SizeAdjustPolicy sizeAdjustPolicy() const;
//此属性保存用于确定用户插入项应出现在组合框中的何处的策略。
void setInsertPolicy(InsertPolicy policy);
InsertPolicy insertPolicy() const;
//此属性保存适合于组合框的最小字符数。
void setMinimumContentsLength(int characters);
int	minimumContentsLength() const;
//此属性保存用户是否可以在组合框中输入重复项。
void setDuplicatesEnabled(bool enable);
bool duplicatesEnabled() const;
//显示弹出
virtual void showPopup();
//隐藏弹出
virtual void hidePopup();
//插入分隔器
void insertSeparator(int index);
//项数量
int	count() const;
```

## QVariant

```c++
QVariant();
...
~QVariant();
bool canConvert(int targetTypeId) const;
bool canConvert() const;
void clear();
bool convert(int targetTypeId);
bool isNull() const;
bool isValid() const;
void setValue(const T & value);
void swap(QVariant & other);
...
Type type() const;
const char * typeName() const;
int userType() const;
T value() const;
bool operator!=(const QVariant & v) const;
bool operator<(const QVariant & v) const;
bool operator<=(const QVariant & v) const;
QVariant & operator=(const QVariant & variant);
QVariant & operator=(QVariant && other);
bool operator==(const QVariant & v) const;
bool operator>(const QVariant & v) const;
bool operator>=(const QVariant & v) const;

QVariant fromValue(const T & value);
Type nameToType(const char * name);
const char * typeToName(int typeId);
```

## QAction

```c++
QAction(QObject * parent);
QAction(const QString & text, QObject * parent);
QAction(const QIcon & icon, const QString & text, QObject * parent);
~QAction();

void setActionGroup(QActionGroup * group);
QActionGroup * actionGroup() const;

void setFont(const QFont & font);
QFont font() const;

void  setIcon(const QIcon & icon);
QIcon icon() const;

void setIconText(const QString & text);
QString	iconText() const;

void setChecked(bool);
bool isChecked() const;

void setCheckable(bool);
bool isCheckable() const;

void setVisible(bool);
bool isVisible() const;

QVariant data() const;
void setData(const QVariant & userData);

void setMenu(QMenu * menu);
QMenu *	menu() const;

void setText(const QString & text);
QString	text() const;

QString	toolTip() const;
void setToolTip(const QString & tip);

QString	whatsThis() const;
void setWhatsThis(const QString & what);

void setDisabled(bool b);
void setEnabled(bool);
bool isEnabled() const;

void setStatusTip(const QString & statusTip);
QString	statusTip() const;

Priority priority() const;
void setPriority(Priority priority);

bool isSeparator() const;
void setSeparator(bool b);

void setMenuRole(MenuRole menuRole);
MenuRole menuRole() const;

void setShortcut(const QKeySequence & shortcut);
QKeySequence shortcut() const;

void setShortcutContext(Qt::ShortcutContext context);
Qt::ShortcutContext	shortcutContext() const;

void setShortcuts(const QList<QKeySequence> & shortcuts);
void setShortcuts(QKeySequence::StandardKey key);
QList<QKeySequence>	shortcuts() const;

QList<QGraphicsWidget *> associatedGraphicsWidgets() const;
QList<QWidget *> associatedWidgets() const;

void setAutoRepeat(bool);
bool autoRepeat() const;

void setIconVisibleInMenu(bool visible);
bool isIconVisibleInMenu() const;

QWidget * parentWidget() const;
void activate(ActionEvent event);
bool showStatusText(QWidget * widget = 0);
void hover();
void toggle();
void trigger();
```

##QActionWidget

```c++
QWidgetAction(QObject * parent);
virtual	~QWidgetAction();
//设置默认窗口
void setDefaultWidget(QWidget * widget);
QWidget * defaultWidget() const;
//释放窗口
void releaseWidget(QWidget * widget);
//请求窗口
QWidget * requestWidget(QWidget * parent);
//创建窗口
virtual QWidget * createWidget(QWidget * parent);
QList<QWidget *> createdWidgets() const;
//删除窗口
virtual void deleteWidget(QWidget * widget);
```

## QLineEdit

```c++
QLineEdit(QWidget * parent = 0);
QLineEdit(const QString & contents, QWidget * parent = 0);
~QLineEdit();
void addAction(QAction * action, ActionPosition position);
QAction * addAction(const QIcon & icon, ActionPosition position);
Qt::Alignment alignment() const;
void backspace();
QCompleter * completer() const;
QMenu *	createStandardContextMenu();
void cursorBackward(bool mark, int steps = 1);
void cursorForward(bool mark, int steps = 1);
Qt::CursorMoveStyle	cursorMoveStyle() const;
int	cursorPosition() const;
int	cursorPositionAt(const QPoint & pos);
void cursorWordBackward(bool mark);
void cursorWordForward(bool mark);
void del();
void deselect();
QString	displayText() const;
bool dragEnabled() const;
EchoMode echoMode() const;
void end(bool mark);
void getTextMargins(int * left, int * top, int * right, int * bottom) const;
bool hasAcceptableInput() const;
bool hasFrame() const;
bool hasSelectedText() const;
void home(bool mark);
QString	inputMask() const;
void insert(const QString & newText);
bool isClearButtonEnabled() const;
bool isModified() const;
bool isReadOnly() const;
bool isRedoAvailable() const;
bool isUndoAvailable() const;
int	maxLength() const;
QString	placeholderText() const;
QString	selectedText() const;
int	selectionStart() const;
void setAlignment(Qt::Alignment flag);
void setClearButtonEnabled(bool enable);
void setCompleter(QCompleter * c);
void setCursorMoveStyle(Qt::CursorMoveStyle style);
void setCursorPosition(int);
void setDragEnabled(bool b);
void setEchoMode(EchoMode);
void setFrame(bool);
void setInputMask(const QString & inputMask);
void setMaxLength(int);
void setModified(bool);
void setPlaceholderText(const QString &);
void setReadOnly(bool);
void setSelection(int start, int length);
void setTextMargins(int left, int top, int right, int bottom);
void setTextMargins(const QMargins & margins);
void setValidator(const QValidator * v);
QString	text() const;
QMargins textMargins() const;
const QValidator * validator() const;      
void copy() const;
void cut();
void paste();
void redo();
void selectAll();
void setText(const QString &);
void undo();
```

## QSpinBox

```c++
QSpinBox(QWidget * parent = 0);
~QSpinBox();

void setValue(int val);
int	value() const;

void setRange(int minimum, int maximum);
void setMaximum(int max);
void setMinimum(int min);
int	maximum() const;
int	minimum() const;

void setSingleStep(int val);
int	singleStep() const;

void setPrefix(const QString & prefix);
void setSuffix(const QString & suffix);
QString	prefix() const;
QString	suffix() const;

int	displayIntegerBase() const;
void setDisplayIntegerBase(int base);

QString	cleanText() const;
```

## QAbstractSlider

```c++
QAbstractSlider(QWidget * parent = 0);
~QAbstractSlider();
//设置最大值，最小值
void setRange(int min, int max);
void setMaximum(int);
void setMinimum(int);
int	maximum() const;
int	minimum() const;
//设置值
void setValue(int);
int	value() const;
void setSliderPosition(int);
int	sliderPosition() const;
//设置单步
void setSingleStep(int);
int	singleStep() const;
//设置页步
void setPageStep(int);
int	pageStep() const;
//设置方向
void setOrientation(Qt::Orientation);
Qt::Orientation	orientation() const;
//此属性保存是否启用滑块跟踪。
void setTracking(bool enable);
bool hasTracking() const;
//滑板是否按下
void setSliderDown(bool);
bool isSliderDown() const;
//此属性用于保存滑块是否显示其反向的值。
void setInvertedAppearance(bool);
bool invertedAppearance() const;
//此属性保存滑块是否反转其滚轮和键事件。
void setInvertedControls(bool);
bool invertedControls() const;
//触发滑块动作。
void triggerAction(SliderAction action);
```

## QLabel

```c++
QLabel(QWidget * parent = 0, Qt::WindowFlags f = 0);
QLabel(const QString & text, QWidget * parent = 0, Qt::WindowFlags f = 0);
~QLabel();

void setAlignment(Qt::Alignment);
Qt::Alignment alignment() const;

void setBuddy(QWidget * buddy);
QWidget * buddy() const;

void setMargin(int);
int	margin() const;

void setSelection(int start, int length);
QString	selectedText() const;
int	selectionStart() const;
bool hasSelectedText() const;

void setTextFormat(Qt::TextFormat);
Qt::TextFormat	textFormat() const;

void setNum(int num);
void setNum(double num);
void setText(const QString &);
QString	text() const;

bool hasScaledContents() const;
void setScaledContents(bool);

void setPicture(const QPicture & picture);
const QPicture * picture() const;

void setPixmap(const QPixmap &);
const QPixmap *	pixmap() const;

void setMovie(QMovie * movie);
QMovie * movie() const;

void setIndent(int);
int	indent() const;

void setOpenExternalLinks(bool open);
bool openExternalLinks() const;

void setWordWrap(bool on);
bool wordWrap() const;

void setTextInteractionFlags(Qt::TextInteractionFlags flags);
Qt::TextInteractionFlags textInteractionFlags() const;

void clear();
```

## QProgressBar

```c++
//构造，析构
QProgressBar(QWidget * parent = 0);
~QProgressBar();
//设置最大，最小值
void setRange(int minimum, int maximum);
void setMaximum(int maximum);
void setMinimum(int minimum);
int	maximum() const;
int	minimum() const;
//设置值，重置
void setValue(int value);
int	value() const;
void reset();
//设置对齐方式
void setAlignment(Qt::Alignment alignment);
Qt::Alignment alignment() const;
//设置格式
void setFormat(const QString & format);
QString	format() const;
void resetFormat();
//设置方向
void setOrientation(Qt::Orientation);
Qt::Orientation	orientation() const;
//设置文本方向
void setTextDirection(QProgressBar::Direction textDirection);
QProgressBar::Direction	textDirection() const;
//设置文本是否可见
void setTextVisible(bool visible);
bool isTextVisible() const;
//颠倒外观
void setInvertedAppearance(bool invert);
bool invertedAppearance() const;
//文本
virtual QString	text() const;
```

## QDockWidget

```c++
//构造，析构
QDockWidget(const QString & title, QWidget * parent = 0, Qt::WindowFlags flags = 0);
QDockWidget(QWidget * parent = 0, Qt::WindowFlags flags = 0);
~QDockWidget();
//设置允许区域
Qt::DockWidgetAreas	allowedAreas() const;
void setAllowedAreas(Qt::DockWidgetAreas areas);
//标题栏窗口
QWidget * titleBarWidget() const;
void setTitleBarWidget(QWidget * widget);
//主窗口
void setWidget(QWidget * widget);
QWidget * widget() const;
//此属性保存dock小部件是否可移动、可关闭和可浮动。
void setFeatures(DockWidgetFeatures features);
DockWidgetFeatures features() const;
//设置浮动
void setFloating(bool floating);
bool isFloating() const;
//是否允许区域
bool isAreaAllowed(Qt::DockWidgetArea area) const;
//触发视图动作
QAction * toggleViewAction() const；
```

## QToolBar

```c++
//构造，析构
QToolBar(const QString & title, QWidget * parent = 0);
QToolBar(QWidget * parent = 0);
~QToolBar();
//添加动作
void addAction(QAction * action);
QAction * addAction(const QString & text);
QAction * addAction(const QIcon & icon, const QString & text);
QAction * addAction(const QString & text, const QObject * receiver, const char * member);
QAction * addAction(const QIcon & icon, const QString & text, const QObject * receiver, const char * member);
//添加窗口
QAction * addWidget(QWidget * widget);
QAction * insertWidget(QAction * before, QWidget * widget);
//添加分离器
QAction * addSeparator();
QAction * insertSeparator(QAction * before);
//动作
QAction * actionAt(const QPoint & p) const;
QAction * actionAt(int x, int y) const;
//浮动
void setFloatable(bool floatable);
bool isFloatable() const;
bool isFloating() const;
//移动
void setMovable(bool movable);
bool isMovable() const;
//图标大小
void setIconSize(const QSize & iconSize);
QSize iconSize() const;
//方向
void setOrientation(Qt::Orientation orientation);
Qt::Orientation	orientation() const;
//停靠区域
void setAllowedAreas(Qt::ToolBarAreas areas);
Qt::ToolBarAreas allowedAreas() const;
bool isAreaAllowed(Qt::ToolBarArea area) const;
//按钮样式
void setToolButtonStyle(Qt::ToolButtonStyle toolButtonStyle);
Qt::ToolButtonStyle	toolButtonStyle() const;
//获取触发动作
QAction * toggleViewAction() const;
//窗口来自动作
QWidget * widgetForAction(QAction * action) const;
//清理
void clear();
```

##  QMenuBar

```c++
//构造，析构
QMenuBar(QWidget * parent = 0);
~QMenuBar();
//添加动作
QAction * addAction(const QString & text);
QAction * addAction(const QString & text, const QObject * receiver, const char * member);
void addAction(QAction * action);
//添加菜单
QAction * addMenu(QMenu * menu);
QMenu *	addMenu(const QString & title);
QMenu *	addMenu(const QIcon & icon, const QString & title);
//添加分割符
QAction * addSeparator();
//插入
QAction * insertMenu(QAction * before, QMenu * menu);
QAction * insertSeparator(QAction * before);
//设置角落窗口
void setCornerWidget(QWidget * widget, Qt::Corner corner = Qt::TopRightCorner);
QWidget * cornerWidget(Qt::Corner corner = Qt::TopRightCorner) const;
//设置弹出方向
void setDefaultUp(bool);
bool isDefaultUp() const;
//设置本地化菜单栏
void setNativeMenuBar(bool nativeMenuBar);
bool isNativeMenuBar() const;
//设置活动动作
void setActiveAction(QAction * act);
QAction * activeAction() const;
//动作
QAction * actionAt(const QPoint & pt) const;
//动作区域
QRect actionGeometry(QAction * act) const;
//设置可见
virtual void setVisible(bool visible);
//清理
void clear();
//ns菜单
NSMenu * toNSMenu();
```

## QMenu

```c++
QMenu(QWidget * parent = 0);
QMenu(const QString & title, QWidget * parent = 0);
~QMenu();
//添加动作
QAction * addAction(const QString & text);
QAction * addAction(const QIcon & icon, const QString & text);
QAction * addAction(const QString & text, const QObject * receiver, const char * member, const QKeySequence & shortcut = 0);
QAction * addAction(const QIcon & icon, const QString & text, const QObject * receiver, const char * member, const QKeySequence & shortcut = 0);
void addAction(QAction * action);
//添加菜单
QAction * addMenu(QMenu * menu);
QMenu *	addMenu(const QString & title);
QMenu *	addMenu(const QIcon & icon, const QString & title);
//添加章节，分割符
QAction * addSection(const QString & text);
QAction * addSection(const QIcon & icon, const QString & text);
QAction * addSeparator();
//插入菜单，章节，分割符
QAction * insertMenu(QAction * before, QMenu * menu);
QAction * insertSection(QAction * before, const QString & text);
QAction * insertSection(QAction * before, const QIcon & icon, const QString & text);
QAction * insertSeparator(QAction * before);
//设置默认动作
void setDefaultAction(QAction * act);
QAction * defaultAction() const;
//标题
void setTitle(const QString & title);
QString	title() const;
//图标
void setIcon(const QIcon & icon);
QIcon icon() const;
//设置活动动作
void setActiveAction(QAction * act);
QAction * activeAction() const;
//是否折叠分割符
void setSeparatorsCollapsible(bool collapse);
bool separatorsCollapsible() const;
//设置工具tip可见
void setToolTipsVisible(bool visible);
bool toolTipsVisible() const;
//菜单被撕下
void setTearOffEnabled(bool);
bool isTearOffEnabled() const;
bool isTearOffMenuVisible() const;
void hideTearOffMenu();
//弹出
QAction * exec();
QAction * exec(const QPoint & p, QAction * action = 0);
//弹出
void popup(const QPoint & p, QAction * atAction = 0);
//动作
QAction * actionAt(const QPoint & pt) const;
//动作区域
QRect actionGeometry(QAction * act) const;
//清理
void clear();
//是否为空
bool isEmpty() const;
//动作
QAction * menuAction() const;
//dock菜单
void setAsDockMenu();
//ns菜单
NSMenu * toNSMenu();
```

## QAbstractItemView

```c++
QAbstractItemView(QWidget *parent = Q_NULLPTR);
~QAbstractItemView();
//委托
QAbstractItemDelegate *itemDelegate() const;
QAbstractItemDelegate *itemDelegate(const QModelIndex &index) const;
QAbstractItemDelegate *itemDelegateForColumn(int column) const;
QAbstractItemDelegate *itemDelegateForRow(int row) const;
void setItemDelegate(QAbstractItemDelegate *delegate);
void setItemDelegateForColumn(int column, QAbstractItemDelegate *delegate);
void setItemDelegateForRow(int row, QAbstractItemDelegate *delegate);
//模型
void openPersistentEditor(const QModelIndex &index);
void closePersistentEditor(const QModelIndex &index);
QModelIndex currentIndex() const;
virtual QModelIndex indexAt(const QPoint &point) const = 0;
QModelIndex rootIndex() const;
void setIndexWidget(const QModelIndex &index, QWidget *widget);
QWidget *indexWidget(const QModelIndex &index) const;
virtual void setModel(QAbstractItemModel *model);
QAbstractItemModel *model() const;
//滚动模式
void setHorizontalScrollMode(ScrollMode mode);
ScrollMode horizontalScrollMode() const;
void resetHorizontalScrollMode();
void setVerticalScrollMode(ScrollMode mode);
ScrollMode verticalScrollMode() const;
void resetVerticalScrollMode();
//自动滚动
bool hasAutoScroll() const;
virtual void scrollTo(const QModelIndex &index, ScrollHint hint = EnsureVisible) = 0;
int autoScrollMargin() const;
void setAutoScroll(bool enable);
void setAutoScrollMargin(int margin);
//选择行为和选择模式
QAbstractItemView::SelectionBehavior selectionBehavior() const;
void setSelectionMode(QAbstractItemView::SelectionMode mode);
virtual void setSelectionModel(QItemSelectionModel *selectionModel);
void setSelectionBehavior(QAbstractItemView::SelectionBehavior behavior);
QAbstractItemView::SelectionMode selectionMode() const;
QItemSelectionModel *selectionModel() const;
//拖放
void setDragEnabled(bool enable);
bool dragEnabled() const;
void setDragDropMode(DragDropMode behavior);
DragDropMode dragDropMode() const;
void setDefaultDropAction(Qt::DropAction dropAction);
Qt::DropAction defaultDropAction() const;
void setDragDropOverwriteMode(bool overwrite);
bool dragDropOverwriteMode() const;
void setDropIndicatorShown(bool enable);
bool showDropIndicator() const;
//替换行
void setAlternatingRowColors(bool enable);
bool alternatingRowColors() const;
//图标大小
void setIconSize(const QSize &size);
QSize iconSize() const;
//编辑触发器
void setEditTriggers(EditTriggers triggers);
EditTriggers editTriggers() const;
//tab key
void setTabKeyNavigation(bool enable);
bool tabKeyNavigation() const;
//省略模式
void setTextElideMode(Qt::TextElideMode mode);
Qt::TextElideMode textElideMode() const;
//大小提示
virtual int sizeHintForColumn(int column) const;
virtual int sizeHintForRow(int row) const;
QSize sizeHintForIndex(const QModelIndex &index) const;
//键盘搜索
virtual void keyboardSearch(const QString &search);
//视觉大小
virtual QRect visualRect(const QModelIndex &index) const = 0;
```

## QChart

```c++
QChart(QGraphicsItem *parent = Q_NULLPTR, Qt::WindowFlags wFlags = Qt::WindowFlags());
~QChart();
void addAxis(QAbstractAxis *axis, Qt::Alignment alignment);
void addSeries(QAbstractSeries *series);
int animationDuration() const;
QEasingCurve animationEasingCurve() const;
AnimationOptions animationOptions() const;
QList<QAbstractAxis *> axes(Qt::Orientations orientation = Qt::Horizontal | Qt::Vertical, QAbstractSeries *series = Q_NULLPTR) const;
QAbstractAxis *axisX(QAbstractSeries *series = Q_NULLPTR) const;
QAbstractAxis *axisY(QAbstractSeries *series = Q_NULLPTR) const;
QBrush backgroundBrush() const;
QPen backgroundPen() const;
qreal backgroundRoundness() const;
ChartType chartType() const;
void createDefaultAxes();
bool isBackgroundVisible() const;
bool isDropShadowEnabled() const;
bool isPlotAreaBackgroundVisible() const;
bool isZoomed();
QLegend *legend() const;
QLocale locale() const;
bool localizeNumbers() const;
QPointF mapToPosition(const QPointF &value, QAbstractSeries *series = Q_NULLPTR);
QPointF mapToValue(const QPointF &position, QAbstractSeries *series = Q_NULLPTR);
QMargins margins() const;
QRectF plotArea() const;
QBrush plotAreaBackgroundBrush() const;
QPen plotAreaBackgroundPen() const;
void removeAllSeries();
void removeAxis(QAbstractAxis *axis);
void removeSeries(QAbstractSeries *series);
void scroll(qreal dx, qreal dy);
QList<QAbstractSeries *> series() const;
void setAnimationDuration(int msecs);
void setAnimationEasingCurve(const QEasingCurve &curve);
void setAnimationOptions(AnimationOptions options);
void setAxisX(QAbstractAxis *axis, QAbstractSeries *series = Q_NULLPTR);
void setAxisY(QAbstractAxis *axis, QAbstractSeries *series = Q_NULLPTR);
void setBackgroundBrush(const QBrush &brush);
void setBackgroundPen(const QPen &pen);
void setBackgroundRoundness(qreal diameter);
void setBackgroundVisible(bool visible = true);
void setDropShadowEnabled(bool enabled = true);
void setLocale(const QLocale &locale);
void setLocalizeNumbers(bool localize);
void setMargins(const QMargins &margins);
void setPlotAreaBackgroundBrush(const QBrush &brush);
void setPlotAreaBackgroundPen(const QPen &pen);
void setPlotAreaBackgroundVisible(bool visible = true);
void setTheme(QChart::ChartTheme theme);
void setTitle(const QString &title);
void setTitleBrush(const QBrush &brush);
void setTitleFont(const QFont &font);
QChart::ChartTheme theme() const;
QString title() const;
QBrush titleBrush() const;
QFont titleFont() const;
void zoom(qreal factor);
void zoomIn();
void zoomIn(const QRectF &rect);
void zoomOut();
void zoomReset();
```

