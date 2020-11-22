output with not all tensors on CUDA:

Traceback (most recent call last):
  File ".\darknet.py", line 308, in <module>
    pred = model(inp, torch.cuda.is_available())
  File "C:\Users\Rene\AppData\Roaming\Python\Python37\site-packages\torch\nn\modules\module.py", line 727, in _call_impl
    result = self.forward(*input, **kwargs)
  File ".\darknet.py", line 288, in forward
    x = predict_transform(x, inp_dim, anchors, num_classes, CUDA)
  File "C:\Users\Rene\Programs\deep_learning\course_project\project\Highway-Montoring-System\util.py", line 48, in predict_transform
    prediction[:,:,:2] += x_y_offset
RuntimeError: Expected all tensors to be on the same device, but found at least two devices, cuda:0 and cpu!



output with wrong height and width:

raceback (most recent call last):
  File ".\darknet.py", line 305, in <module>
    pred = model(inp, torch.cuda.is_available())
  File "C:\Users\Rene\AppData\Roaming\Python\Python37\site-packages\torch\nn\modules\module.py", line 727, in _call_impl
    result = self.forward(*input, **kwargs)
  File ".\darknet.py", line 288, in forward
    x = predict_transform(x, inp_dim, anchors, num_classes, CUDA)
  File "C:\Users\Rene\Programs\deep_learning\course_project\project\Highway-Montoring-System\util.py", line 19, in predict_transform
    prediction = prediction.view(batch_size, bbox_attrs*num_anchors, grid_size*grid_size)
RuntimeError: shape '[1, 255, 3025]' is invalid for input of size 689520


output before weights are loaded:

tensor([[[1.7510e+01, 1.3686e+01, 7.7607e+01,  ..., 6.1217e-01,
          5.2269e-01, 5.5511e-01],
         [1.4250e+01, 1.7545e+01, 1.3528e+02,  ..., 5.3071e-01,
          4.6039e-01, 5.5613e-01],
         [1.5576e+01, 1.5151e+01, 4.5846e+02,  ..., 5.1155e-01,
          5.7344e-01, 6.2045e-01],
         ...,
         [4.1212e+02, 4.1150e+02, 1.1054e+01,  ..., 4.7634e-01,
          4.4970e-01, 4.9296e-01],
         [4.1169e+02, 4.1214e+02, 2.1055e+01,  ..., 5.0062e-01,
          5.3064e-01, 4.5293e-01],
         [4.1212e+02, 4.1203e+02, 3.5794e+01,  ..., 5.0944e-01,
          4.5806e-01, 4.6678e-01]]], device='cuda:0')
torch.Size([1, 10647, 85])

output after weights are loaded:
tensor([[[8.5426e+00, 1.9015e+01, 1.1130e+02,  ..., 1.7306e-03,
          1.3874e-03, 9.2985e-04],
         [1.4105e+01, 1.8867e+01, 9.4014e+01,  ..., 5.9501e-04,
          9.2471e-04, 1.3085e-03],
         [2.1125e+01, 1.5269e+01, 3.5793e+02,  ..., 8.3609e-03,
          5.1067e-03, 5.8562e-03],
         ...,
         [4.1253e+02, 4.1022e+02, 3.8228e+00,  ..., 4.0967e-06,
          5.6907e-06, 1.3153e-06],
         [4.1074e+02, 4.0990e+02, 8.4218e+00,  ..., 3.8752e-05,
          5.0833e-05, 2.4754e-05],
         [4.1037e+02, 4.1262e+02, 4.5173e+01,  ..., 1.5562e-05,
          1.8985e-05, 3.0373e-05]]], device='cuda:0')
torch.Size([1, 10647, 85])