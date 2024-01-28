### Environment Setup

```she
# Login
Use SSH with the given username and 2FA key to login HACC@NUS
ssh username@xacchead.d2.comp.nus.edu.sg

# Interactive access commands for nodes
srun -p mi100 --pty bash -i

```



### Hip Programming Guide

```she
# Copy source file to user space
cp -r /data/papatheodore/introduction_to_hip ./
# Running
cd introduction_to_hip/

# For the examples lab, the source code is the corresponding ***.cpp file
cd examples/
cd 0*_*****
sbatch submit.sh
cat slurm-*****.out

# For the exercises lab, try modifying the source code yourself first to meet the corresponding requirements. The solution code is in the solution folder
cd exercises/
cd 0*_*****
cd solution
sbatch submit.sh
cat slurm-*****.out
```

