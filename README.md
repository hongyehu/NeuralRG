

# Real NVP 

## How to Run 

```python
#ring2D
python learn_realnvp.py -Batch 64 -Ntherm 10 -Nsteps 10 -Nskip 10 -Nlayers 4 -Hs 10 -Ht 10 -target ring2d -epsilon 1.0 -alpha 0.0 -beta 1.0 -delta 1.0 -omega 1.0 -Nepoch 5000 

#Ising
python learn_realnvp.py -Batch 64 -Ntherm 5 -Nsteps 1 -Nskip 0 -Nlayers 10 -Hs 4 -Ht 4 -target ising -T 2.5 -L 8 -d 2 -epsilon 1.0 -beta 1.0  -delta 1.0 -omega 0.0  -Nepoch 5000 -lr 0.001 -exact 0.177921 -train_model 

#or 
python learn_realnvp.py -Batch 256 -Ntherm 0 -Nsteps 5 -Nskip 0 -Nlayers 8 -Hs 16 -Ht 16 -target ising -T 2.5 -L 8 -d 2 -epsilon 0.0 -beta 1.0  -delta 0.0 -omega 1.0  -Nepoch 1000 -lr 0.001 -exact 0.177921 -train_model

#or 
python learn_tebd.py -Batch 256 -Ntherm 0 -Nsteps 5 -Nskip 0 -Nlayers 8 -Hs 16 -Ht 16 -target ising -T 2.5 -L 16 -d 1 -epsilon 0.0 -beta 1.0  -delta 0.0 -omega 1.0  -Nepoch 1000 -lr 0.001 -exact 0.138871 -train_model
```

To check the results 

```python
#sample using the model
python learn_accratio.py -Batch 64 -Ntherm 5 -Nsteps 1 -Nskip 0 -Nlayers 10 -Hs 4 -Ht 4 -target ising -K 0.44068679350977147 -L 4 -d 2 -epsilon 1.0 -beta 1.0  -delta 1.0 -omega 0.0  -Nepoch 5000 -lr 0.01 -exact 0.371232 -modelname data/learn_acc/ising_L4_d2_K0.44068679350977147_Nl10_Hs4_Ht4_epsilon1.0_beta1.0_delta1.0_omega0.0_Batchsize64_Ntherm5_Nsteps1_Nskips0_lr0.01/epoch230

# plot proposed and accepted configurations
python plot_configs.py -f data/learn_acc/ising_L4_d2_K0.44068679350977147_Nl10_Hs4_Ht4_epsilon1.0_beta1.0_delta1.0_omega0.0_Batchsize64_Ntherm5_Nsteps1_Nskips0_lr0.01_mc.h5 

```

### Exact Ising results 

| $d=1,T=2.5$ |          PBC          |         OBC          |
| :---------: | :-------------------: | :------------------: |
|    $L=8$    |  0.277838+/-0.000294  |                      |
|   $L=16$    |  0.138871+/-0.000273  | 0.130933+/-0.000262  |
|   $L=64$    | 0.0344761+/-0.0001465 | 0.0341328+/-0.000158 |



| $d=2,T=T_c$ |          PBC          |          OBC          |
| :---------: | :-------------------: | :-------------------: |
|    $L=2$    |                       | 0.56882 +/- 0.000409  |
|    $L=4$    | 0.761761 +/- 0.000421 | 0.371232 +/- 0.000429 |
|    $L=6$    | 0.693504 +/- 0.000436 | 0.30321 +/- 0.000397  |
|    $L=8$    | 0.646769 +/- 0.000445 | 0.266751 +/- 0.00038  |

| $d=2,T=2.5$ | PBC  |          OBC           |
| :---------: | :--: | :--------------------: |
|    $L=4$    |      |   0.309222+/-0.0004    |
|    $L=8$    |      | 0.177921 +/- 0.000304  |
|   $L=16$    |      | 0.0905703 +/- 0.000219 |






