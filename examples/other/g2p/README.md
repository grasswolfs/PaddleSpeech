# G2P
For g2p, we use BZNSYP's phone label as the ground truth and we delete silence tokens in labels and predicted phones.

You should Download BZNSYP from it's [Official Website](https://test.data-baker.com/data/index/source) and extract it. Assume the path to the dataset is `~/datasets/BZNSYP`.

We use `WER` as evaluation criterion.

# Start
Run the command below to get the results of test.
```bash
./run.sh
```
The `avg WER` of g2p is: 0.027495061517943988
```text
     ,--------------------------------------------------------------------.
     |        | # Snt    # Wrd  | Corr    Sub    Del    Ins    Err  S.Err |
     |--------+-----------------+-----------------------------------------|
     | Sum/Avg|  9996   299181  | 97.3    2.7    0.0    0.0    2.7   52.5 |
     `--------------------------------------------------------------------'
```
