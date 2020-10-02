## QSettings

```c++
QSettings(const QString &organization, const QString &application = QString(), QObject *parent = Q_NULLPTR);
QSettings(Scope scope, const QString &organization, const QString &application = QString(), QObject *parent = Q_NULLPTR);
QSettings(Format format, Scope scope, const QString &organization, const QString &application = QString(), QObject *parent = Q_NULLPTR);
QSettings(const QString &fileName, Format format, QObject *parent = Q_NULLPTR)；
QSettings(QObject *parent = Q_NULLPTR);
~QSettings();

QString applicationName() const;
QString organizationName() const;

QStringList allKeys() const；

QString group() const;
void beginGroup(const QString &prefix);
int beginReadArray(const QString &prefix);
void beginWriteArray(const QString &prefix, int size = -1);
void endArray();
void endGroup();
QStringList childGroups() const;
QStringList childKeys() const;

void clear();
bool contains(const QString &key) const;
void remove(const QString &key);
void setValue(const QString &key, const QVariant &value);
QVariant value(const QString &key, const QVariant &defaultValue = QVariant()) const;  

void setFallbacksEnabled(bool b);
bool fallbacksEnabled() const;
Status status() const;
void sync();
bool isWritable() const;

Format registerFormat(const QString &extension, ReadFunc readFunc, WriteFunc writeFunc, Qt::CaseSensitivity caseSensitivity = Qt::CaseSensitive);
void setDefaultFormat(Format format);
Format defaultFormat();
Format format() const;

void setIniCodec(QTextCodec *codec);
void setIniCodec(const char *codecName);
QTextCodec *iniCodec() const;

QString fileName() const;
void setPath(Format format, Scope scope, const QString &path);

Scope scope() const;
void setArrayIndex(int i);
```

## QGraphicsScene

```c++
QGraphicsScene(QObject *parent = Q_NULLPTR);
QGraphicsScene(const QRectF &sceneRect, QObject *parent = Q_NULLPTR);
QGraphicsScene(qreal x, qreal y, qreal width, qreal height, QObject *parent = Q_NULLPTR);
virtual ~QGraphicsScene();

QGraphicsItem *activePanel() const;
QGraphicsWidget *activeWindow() const;

QGraphicsEllipseItem *addEllipse(const QRectF &rect, const QPen &pen = QPen(), const QBrush &brush = QBrush());
QGraphicsEllipseItem *addEllipse(qreal x, qreal y, qreal w, qreal h, const QPen &pen = QPen(), const QBrush &brush = QBrush());
void addItem(QGraphicsItem *item);
QGraphicsLineItem *addLine(const QLineF &line, const QPen &pen = QPen());
QGraphicsLineItem *addLine(qreal x1, qreal y1, qreal x2, qreal y2, const QPen &pen = QPen());
QGraphicsPathItem *addPath(const QPainterPath &path, const QPen &pen = QPen(), const QBrush &brush = QBrush());
QGraphicsPixmapItem *addPixmap(const QPixmap &pixmap);
QGraphicsPolygonItem *addPolygon(const QPolygonF &polygon, const QPen &pen = QPen(), const QBrush &brush = QBrush());
QGraphicsRectItem *addRect(const QRectF &rect, const QPen &pen = QPen(), const QBrush &brush = QBrush());
QGraphicsRectItem *addRect(qreal x, qreal y, qreal w, qreal h, const QPen &pen = QPen(), const QBrush &brush = QBrush());
QGraphicsSimpleTextItem *addSimpleText(const QString &text, const QFont &font = QFont());
QGraphicsTextItem *addText(const QString &text, const QFont &font = QFont());
QGraphicsProxyWidget *addWidget(QWidget *widget, Qt::WindowFlags wFlags = Qt::WindowFlags());

QBrush backgroundBrush() const;
int bspTreeDepth() const;
void clearFocus();
QList<QGraphicsItem *> collidingItems(const QGraphicsItem *item, Qt::ItemSelectionMode mode = Qt::IntersectsItemShape) const;
QGraphicsItemGroup *createItemGroup(const QList<QGraphicsItem *> &items);
void destroyItemGroup(QGraphicsItemGroup *group);
QGraphicsItem *focusItem() const;
QFont font() const;
QBrush foregroundBrush() const;
bool hasFocus() const;
qreal height() const;
virtual QVariant inputMethodQuery(Qt::InputMethodQuery query) const;
void invalidate(qreal x, qreal y, qreal w, qreal h, SceneLayers layers = AllLayers);
bool isActive() const;

QGraphicsItem *itemAt(const QPointF &position, const QTransform &deviceTransform) const;
QGraphicsItem *itemAt(qreal x, qreal y, const QTransform &deviceTransform) const;
ItemIndexMethod itemIndexMethod() const;
QList<QGraphicsItem *> items(Qt::SortOrder order = Qt::DescendingOrder) const;
QList<QGraphicsItem *> items(const QPointF &pos, Qt::ItemSelectionMode mode = Qt::IntersectsItemShape, Qt::SortOrder order = Qt::DescendingOrder, const QTransform &deviceTransform = QTransform()) const;
QList<QGraphicsItem *> items(const QRectF &rect, Qt::ItemSelectionMode mode = Qt::IntersectsItemShape, Qt::SortOrder order = Qt::DescendingOrder, const QTransform &deviceTransform = QTransform()) const;
QList<QGraphicsItem *> items(const QPolygonF &polygon, Qt::ItemSelectionMode mode = Qt::IntersectsItemShape, Qt::SortOrder order = Qt::DescendingOrder, const QTransform &deviceTransform = QTransform()) const;
QList<QGraphicsItem *> items(const QPainterPath &path, Qt::ItemSelectionMode mode = Qt::IntersectsItemShape, Qt::SortOrder order = Qt::DescendingOrder, const QTransform &deviceTransform = QTransform()) const;
QList<QGraphicsItem *> items(qreal x, qreal y, qreal w, qreal h, Qt::ItemSelectionMode mode, Qt::SortOrder order, const QTransform &deviceTransform = QTransform()) const;

QRectF itemsBoundingRect() const;
qreal minimumRenderSize() const;
QGraphicsItem *mouseGrabberItem() const;
QPalette palette() const;
void removeItem(QGraphicsItem *item);
void render(QPainter *painter, const QRectF &target = QRectF(), const QRectF &source = QRectF(), Qt::AspectRatioMode aspectRatioMode = Qt::KeepAspectRatio);
QRectF sceneRect() const;
QList<QGraphicsItem *> selectedItems() const;
QPainterPath selectionArea() const;
bool sendEvent(QGraphicsItem *item, QEvent *event);
void setActivePanel(QGraphicsItem *item);
void setActiveWindow(QGraphicsWidget *widget);
void setBackgroundBrush(const QBrush &brush);
void setBspTreeDepth(int depth);
void setFocus(Qt::FocusReason focusReason = Qt::OtherFocusReason);
void setFocusItem(QGraphicsItem *item, Qt::FocusReason focusReason = Qt::OtherFocusReason);
void setFont(const QFont &font);
void setForegroundBrush(const QBrush &brush);
void setItemIndexMethod(ItemIndexMethod method);
void setMinimumRenderSize(qreal minSize);
void setPalette(const QPalette &palette);
void setSceneRect(const QRectF &rect);
void setSceneRect(qreal x, qreal y, qreal w, qreal h);
void setSelectionArea(const QPainterPath &path, const QTransform &deviceTransform);
void setSelectionArea(const QPainterPath &path, Qt::ItemSelectionMode mode = Qt::IntersectsItemShape, const QTransform &deviceTransform = QTransform());
void setSelectionArea(const QPainterPath &path, Qt::ItemSelectionOperation selectionOperation, Qt::ItemSelectionMode mode = Qt::IntersectsItemShape, const QTransform &deviceTransform = QTransform());
void setStickyFocus(bool enabled);
void setStyle(QStyle *style);
bool stickyFocus() const;
QStyle *style() const;
void update(qreal x, qreal y, qreal w, qreal h);
QList<QGraphicsView *> views() const;
qreal width() const;
```

## QGraphicsItem

```c++
QGraphicsItem(QGraphicsItem *parent = Q_NULLPTR);
virtual ~QGraphicsItem();
bool acceptDrops() const;
bool acceptHoverEvents() const;
bool acceptTouchEvents() const;
Qt::MouseButtons acceptedMouseButtons() const;
virtual void advance(int phase);
virtual QRectF boundingRect() const = 0;
QRegion boundingRegion(const QTransform &itemToDeviceTransform) const;
qreal boundingRegionGranularity() const;
CacheMode cacheMode() const;
QList<QGraphicsItem *> childItems() const;
QRectF childrenBoundingRect() const;
void clearFocus();
QPainterPath clipPath() const;
virtual bool collidesWithItem(const QGraphicsItem *other, Qt::ItemSelectionMode mode = Qt::IntersectsItemShape) const;
virtual bool collidesWithPath(const QPainterPath &path, Qt::ItemSelectionMode mode = Qt::IntersectsItemShape) const;
QList<QGraphicsItem *> collidingItems(Qt::ItemSelectionMode mode = Qt::IntersectsItemShape) const;
QGraphicsItem *commonAncestorItem(const QGraphicsItem *other) const;
virtual bool contains(const QPointF &point) const;
QCursor cursor() const;
QVariant data(int key) const;
QTransform deviceTransform(const QTransform &viewportTransform) const;
qreal effectiveOpacity() const;
void ensureVisible(const QRectF &rect = QRectF(), int xmargin = 50, int ymargin = 50);
void ensureVisible(qreal x, qreal y, qreal w, qreal h, int xmargin = 50, int ymargin = 50);
bool filtersChildEvents() const;
GraphicsItemFlags flags() const;
QGraphicsItem *focusItem() const;
QGraphicsItem *focusProxy() const;
void grabKeyboard();
void grabMouse();
QGraphicsEffect *graphicsEffect() const;
QGraphicsItemGroup *group() const;
bool hasCursor() const;
bool hasFocus() const;
void hide();
Qt::InputMethodHints inputMethodHints() const;
void installSceneEventFilter(QGraphicsItem *filterItem);
bool isActive() const;
bool isAncestorOf(const QGraphicsItem *child) const;
bool isBlockedByModalPanel(QGraphicsItem **blockingPanel = Q_NULLPTR) const;
bool isClipped() const;
bool isEnabled() const;
bool isObscured(const QRectF &rect = QRectF()) const;
bool isObscured(qreal x, qreal y, qreal w, qreal h) const;
virtual bool isObscuredBy(const QGraphicsItem *item) const;
bool isPanel() const;
bool isSelected() const;
bool isUnderMouse() const;
bool isVisible() const;
bool isVisibleTo(const QGraphicsItem *parent) const;
bool isWidget() const;
bool isWindow() const;

QTransform itemTransform(const QGraphicsItem *other, bool *ok = Q_NULLPTR) const;
QPointF mapFromItem(const QGraphicsItem *item, const QPointF &point) const;
QPolygonF mapFromItem(const QGraphicsItem *item, const QRectF &rect) const;
QPolygonF mapFromItem(const QGraphicsItem *item, const QPolygonF &polygon) const;
QPainterPath mapFromItem(const QGraphicsItem *item, const QPainterPath &path) const;
QPointF mapFromItem(const QGraphicsItem *item, qreal x, qreal y) const;
QPolygonF mapFromItem(const QGraphicsItem *item, qreal x, qreal y, qreal w, qreal h) const;

QPointF mapFromParent(const QPointF &point) const;
QPolygonF mapFromParent(const QRectF &rect) const
QPolygonF mapFromParent(const QPolygonF &polygon) const
QPainterPath mapFromParent(const QPainterPath &path) const
QPointF mapFromParent(qreal x, qreal y) const
QPolygonF mapFromParent(qreal x, qreal y, qreal w, qreal h) const

QPointF mapFromScene(const QPointF &point) const
QPolygonF mapFromScene(const QRectF &rect) const
QPolygonF mapFromScene(const QPolygonF &polygon) const
QPainterPath mapFromScene(const QPainterPath &path) const
QPointF mapFromScene(qreal x, qreal y) const
QPolygonF mapFromScene(qreal x, qreal y, qreal w, qreal h) const
QRectF mapRectFromItem(const QGraphicsItem *item, const QRectF &rect) const
QRectF mapRectFromItem(const QGraphicsItem *item, qreal x, qreal y, qreal w, qreal h) const;

QRectF mapRectFromParent(const QRectF &rect) const
QRectF mapRectFromParent(qreal x, qreal y, qreal w, qreal h) const
QRectF mapRectFromScene(const QRectF &rect) const
QRectF mapRectFromScene(qreal x, qreal y, qreal w, qreal h) const
QRectF mapRectToItem(const QGraphicsItem *item, const QRectF &rect) const
QRectF mapRectToItem(const QGraphicsItem *item, qreal x, qreal y, qreal w, qreal h) const
QRectF mapRectToParent(const QRectF &rect) const
QRectF mapRectToParent(qreal x, qreal y, qreal w, qreal h) const;

QRectF mapRectToScene(const QRectF &rect) const
QRectF mapRectToScene(qreal x, qreal y, qreal w, qreal h) const;

QPointF mapToItem(const QGraphicsItem *item, const QPointF &point) const
QPolygonF mapToItem(const QGraphicsItem *item, const QRectF &rect) const
QPolygonF mapToItem(const QGraphicsItem *item, const QPolygonF &polygon) const
QPainterPath mapToItem(const QGraphicsItem *item, const QPainterPath &path) const
QPointF mapToItem(const QGraphicsItem *item, qreal x, qreal y) const
QPolygonF mapToItem(const QGraphicsItem *item, qreal x, qreal y, qreal w, qreal h) const;

QPointF mapToParent(const QPointF &point) const
QPolygonF mapToParent(const QRectF &rect) const
QPolygonF mapToParent(const QPolygonF &polygon) const
QPainterPath mapToParent(const QPainterPath &path) const
QPointF mapToParent(qreal x, qreal y) const
QPolygonF mapToParent(qreal x, qreal y, qreal w, qreal h) const;

QPointF mapToScene(const QPointF &point) const
QPolygonF mapToScene(const QRectF &rect) const
QPolygonF mapToScene(const QPolygonF &polygon) const
QPainterPath mapToScene(const QPainterPath &path) const
QPointF mapToScene(qreal x, qreal y) const
QPolygonF mapToScene(qreal x, qreal y, qreal w, qreal h) const;

void moveBy(qreal dx, qreal dy)
qreal opacity() const
virtual QPainterPath opaqueArea() const
virtual void paint(QPainter *painter, const QStyleOptionGraphicsItem *option, QWidget *widget = Q_NULLPTR) = 0
QGraphicsItem *panel() const
PanelModality panelModality() const
QGraphicsItem *parentItem() const
QGraphicsObject *parentObject() const
QGraphicsWidget *parentWidget() const
QPointF pos() const
void removeSceneEventFilter(QGraphicsItem *filterItem)
void resetTransform()
qreal rotation() const
qreal scale() const
QGraphicsScene *scene() const
QRectF sceneBoundingRect() const
QPointF scenePos() const
QTransform sceneTransform() const
void scroll(qreal dx, qreal dy, const QRectF &rect = QRectF())
void setAcceptDrops(bool on)
void setAcceptHoverEvents(bool enabled)
void setAcceptTouchEvents(bool enabled)
void setAcceptedMouseButtons(Qt::MouseButtons buttons)
void setActive(bool active)
void setBoundingRegionGranularity(qreal granularity)
void setCacheMode(CacheMode mode, const QSize &logicalCacheSize = QSize())
void setCursor(const QCursor &cursor)
void setData(int key, const QVariant &value)
void setEnabled(bool enabled)
void setFiltersChildEvents(bool enabled)
void setFlag(GraphicsItemFlag flag, bool enabled = true)
void setFlags(GraphicsItemFlags flags)
void setFocus(Qt::FocusReason focusReason = Qt::OtherFocusReason)
void setFocusProxy(QGraphicsItem *item)
void setGraphicsEffect(QGraphicsEffect *effect)
void setGroup(QGraphicsItemGroup *group)
void setInputMethodHints(Qt::InputMethodHints hints)
void setOpacity(qreal opacity)
void setPanelModality(PanelModality panelModality)
void setParentItem(QGraphicsItem *newParent)
void setPos(const QPointF &pos)
void setPos(qreal x, qreal y)
void setRotation(qreal angle)
void setScale(qreal factor)
void setSelected(bool selected)
void setToolTip(const QString &toolTip)
void setTransform(const QTransform &matrix, bool combine = false)
void setTransformOriginPoint(const QPointF &origin)
void setTransformOriginPoint(qreal x, qreal y)
void setTransformations(const QList<QGraphicsTransform *> &transformations)
void setVisible(bool visible)
void setX(qreal x)
void setY(qreal y)
void setZValue(qreal z)
virtual QPainterPath shape() const
void show()
void stackBefore(const QGraphicsItem *sibling)
QGraphicsObject *toGraphicsObject()
const QGraphicsObject *toGraphicsObject() const
QString toolTip() const
QGraphicsItem *topLevelItem() const
QGraphicsWidget *topLevelWidget() const
QTransform transform() const
QPointF transformOriginPoint() const
QList<QGraphicsTransform *> transformations() const
virtual int type() const
void ungrabKeyboard()
void ungrabMouse()
void unsetCursor()
void update(const QRectF &rect = QRectF())
void update(qreal x, qreal y, qreal width, qreal height)
QGraphicsWidget *window() const
qreal x() const
qreal y() const
qreal zValue() const;
```
