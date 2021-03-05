# Transferring Dense Pose to Proximal Animal Classes 
**Artsiom Sanakoyeu, Vasil Khalidov, Maureen S. McCarthy, Andrea Vedaldi, Natalia Neverova**,
***In CVPR 2020*** 


🌐 **Project page**: https://asanakoy.github.io/densepose-evolution/  
📝 **Paper pdf**: https://arxiv.org/pdf/2003.00080.pdf

### News
**04.03.2021.** Source code fo our method was published as a part of [Detectron2 library](https://github.com/facebookresearch/detectron2/tree/master/projects/DensePose).

# Source code

### DenseposeEvolution Models & Bootstrapping Pipeline 
![image](https://user-images.githubusercontent.com/1690869/110182908-04cb3400-7e0e-11eb-8f43-616a664fdc28.png)

We introduced a pipeline
to transfer DensePose models trained on humans to proximal animal classes (chimpanzees),
which is summarized in Figure 3. The training proceeds in two stages:

First, a *master* model is trained on data from source domain (humans with full
DensePose annotation `S`, `I`, `U` and `V`)
and supporting domain (animals with segmentation annotation only).
Only selected animal classes are chosen from the supporting
domain through *category filters* to guarantee the quality of target domain results.
The training is done in *class-agnostic manner*: all selected categories are mapped
to a single category (human).

Second, a *student* model is trained on data from source and supporting domains,
as well as data from target domain obtained by applying the master model, selecting
high-confidence detections and sampling the results.


Examples of **pretrained master and student models** are available in the [Model Zoo](https://github.com/facebookresearch/detectron2/blob/master/projects/DensePose/doc/DENSEPOSE_IUV.md#ModelZooBootstrap). 

For more **details on the bootstrapping pipeline and how to train**, please see [Bootstrapping Pipeline README](https://github.com/facebookresearch/detectron2/blob/master/projects/DensePose/doc/BOOTSTRAPPING_PIPELINE.md).


## <a name="References"></a> References

If you use our method, please take the references from the following
BibTeX entries:

DenseposeEvolution bootstrapping pipeline:
```
@InProceedings{Sanakoyeu2020TransferringDensePose,
    title = {Transferring Dense Pose to Proximal Animal Classes},
    author = {Artsiom Sanakoyeu and Vasil Khalidov and Maureen S. McCarthy and Andrea Vedaldi and Natalia Neverova},
    journal = {The IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
    year = {2020},
}
```

DensePose with confidence estimation:
```
@InProceedings{Neverova2019DensePoseConfidences,
    title = {Correlated Uncertainty for Learning Dense Correspondences from Noisy Labels},
    author = {Neverova, Natalia and Novotny, David and Vedaldi, Andrea},
    journal = {Advances in Neural Information Processing Systems},
    year = {2019},
}
```

Original DensePose:
```
@InProceedings{Guler2018DensePose,
  title={DensePose: Dense Human Pose Estimation In The Wild},
  author={R\{i}za Alp G\"uler, Natalia Neverova, Iasonas Kokkinos},
  journal={The IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
  year={2018}
}
```
