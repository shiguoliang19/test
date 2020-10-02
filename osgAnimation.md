# OSG动画学习

## Keyframe 关键帧

```c++
double  getTime () const;
void  setTime (double time);
```

## Interpolator 插值器

```c++
Interpolator();
Interpolator(const Interpolator &copy, const osg::CopyOp &copyop=osg::CopyOp::SHALLOW_COPY);
virtual const char* libraryName() const;
virtual const char* className () const;
virtual bool isSameKindAs (const osg::Object *obj) const;
virtual float interpolate(float t, float y1, float y2) const=0;
virtual osg::Vec2 interpolate(float t, const osg::Vec2 &y1, const osg::Vec2 &y2) const; 
virtual osg::Vec3 interpolate(float t, const osg::Vec3 &y1, const osg::Vec3 &y2) const;
virtual osg::Vec4 interpolate (float t, const osg::Vec4 &y1, const osg::Vec4 &y2) const;
template<class ValueType>ValueType interpolate (float t, const range< ValueType > &r) const;
```

##  KeyframeContainer 关键帧容器

```c++
KeyframeContainer();
~KeyframeContainer(); 
virtual unsigned int size() const=0;
```

## Sampler 釆样器

```c++
virtual KeyframeContainer* getKeyframeContainer()=0;
virtual const KeyframeContainer* getKeyframeContainer () const =0;

TemplateSampler();
~TemplateSampler();  
void getValueAt(double time, UsingType &result) const;
void setKeyframeContainer(KeyframeContainerType *kf);
virtual KeyframeContainer* getKeyframeContainer();
virtual const KeyframeContainer* getKeyframeContainer() const;
KeyframeContainerType* getKeyframeContainerTyped();
const KeyframeContainerType* getKeyframeContainerTyped() const;
KeyframeContainerType* getOrCreateKeyframeContainer();
double getStartTime() const;
double getEndTime() const;
```

## Channel 频道

```c++
Channel();
Channel(const Channel &channel);
virtual ~Channel();
virtual Channel* clone() const=0;
virtual void update(double time,float weight,int priority)=0;
virtual void reset()=0;
virtual Target* getTarget()=0;
virtual bool setTarget(Target *)=0;
const std::string& getName() const;
void setName(const std::string &name);
virtual double getStartTime() const=0;
virtual double getEndTime() const=0;
const std::string& getTargetName() const;
void setTargetName(const std::string &name);
virtual Sampler* getSampler()=0;
virtual const Sampler* getSampler() const=0;
virtual bool createKeyframeContainerFromTargetValue()=0;
```

## Animation 动画

```c++
META_Object(osgAnimation, Animation) Animation();
Animation(const osgAnimation::Animation &, const osg::CopyOp &);
void  addChannel(Channel *pChannel); 
ChannelList& getChannels();
const ChannelList& getChannels() const;
void setDuration(double duration);
void computeDuration();
double getDuration() const;
void setWeight(float weight);
float getWeight() const;
bool update(double time, int priority=0);
void resetTargets();
void setPlayMode(PlayMode mode);
PlayMode getPlayMode() const;
void setStartTime(double time);
double getStartTime() const;
```

## AnimationManagerBase 动画管理

```c++
AnimationManagerBase();
AnimationManagerBase(const AnimationManagerBase &b, const osg::CopyOp &copyop=osg::CopyOp::SHALLOW_COPY);
virtual ~AnimationManagerBase();
virtual void buildTargetReference();
virtual void registerAnimation(Animation *);
virtual void unregisterAnimation(Animation *);
virtual void link(osg::Node *subgraph);
virtual void update(double t)=0;
virtual bool needToLink() const;
const AnimationList & getAnimationList() const;
virtual void operator()(osg::Node *node, osg::NodeVisitor *nv);
void clearTargets();
LinkVisitor* getOrCreateLinkVisitor();
void setLinkVisitor(LinkVisitor *);
void setAutomaticLink(bool);
bool getAutomaticLink() const;
bool isAutomaticLink() const;
void dirty();

META_Object(osgAnimation, BasicAnimationManager);
BasicAnimationManager();
BasicAnimationManager(const AnimationManagerBase &b, const osg::CopyOp &copyop=osg::CopyOp::SHALLOW_COPY);
virtual ~BasicAnimationManager();
void update(double time);
void playAnimation(Animation *pAnimation, int priority=0, float weight=1.0);
bool stopAnimation(Animation *pAnimation);
bool findAnimation(Animation *pAnimation);
bool isPlaying(Animation *pAnimation);
bool isPlaying(const std::string &animationName); 
void stopAll();
```
