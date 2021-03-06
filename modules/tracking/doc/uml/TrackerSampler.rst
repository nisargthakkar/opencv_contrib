TrackerSampler diagram
======================

.. uml::

  ..@startuml
  package "TrackerSampler package" #DDDDDD {

  class TrackerSampler{
    -vector<pair<String, Ptr<TrackerSamplerAlgorithm> > > samplers
    -vector<Mat> samples;
    ...
    TrackerSampler();
    ~TrackerSampler();
    +sampling(const Mat& image, Rect boundingBox);
    +const vector<pair<String, Ptr<TrackerSamplerAlgorithm> > >& getSamplers();
    +const vector<Mat>& getSamples();
    +bool addTrackerSamplerAlgorithm(String trackerSamplerAlgorithmType);
    +bool addTrackerSamplerAlgorithm(Ptr<TrackerSamplerAlgorithm>& sampler);
    ---
    -void clearSamples();
  }

  class TrackerSamplerAlgorithm{
    ~TrackerSamplerAlgorithm();
    +static Ptr<TrackerSamplerAlgorithm> create(const String& trackerSamplerType);
    +bool sampling(const Mat& image, Rect boundingBox, vector<Mat>& sample);
  }
  note bottom: A tracker could sample the target\nor it could sample the target and the background


  class TrackerSamplerCS{
    TrackerSamplerCS();
    ~TrackerSamplerCS();
    +bool sampling(const Mat& image, Rect boundingBox, vector<Mat>& sample);
  }
  class TrackerSamplerCSC{
    TrackerSamplerCSC();
    ~TrackerSamplerCSC();
    +bool sampling(const Mat& image, Rect boundingBox, vector<Mat>& sample);
  }


  }
  ..@enduml
