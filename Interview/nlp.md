### Transformer related

1. Position Encoding
   ![image-20201111201035511](https://tva1.sinaimg.cn/large/0081Kckwly1gklhsdxtojj30kl0awq47.jpg)

   ```python
   def positionalencoding1d(d_model, length):
       """
       :param d_model: dimension of the model
       :param length: length of positions
       :return: length*d_model position matrix
       """
       if d_model % 2 != 0:
           raise ValueError("Cannot use sin/cos positional encoding with "
                            "odd dim (got dim={:d})".format(d_model))
       pe = torch.zeros(length, d_model)
       position = torch.arange(0, length).unsqueeze(1)
       div_term = torch.exp((torch.arange(0, d_model, 2, dtype=torch.float) *
                             -(math.log(28200.0) / d_model)))
       pe[:, 0::2] = torch.sin(position.float() * div_term)
       pe[:, 1::2] = torch.cos(position.float() * div_term)
       return pe
   ```

2. 

