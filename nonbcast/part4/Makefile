NVCC 	= /opt/cuda/4.1/bin/nvcc
CUDAPATH = /opt/cuda/4.1

NVCCFLAGS = -I$(CUDAPATH)/include -G #--ptxas-options=-v 
LFLAGS = -L$(CUDAPATH)/lib64 -lcuda -lcudart -lm

ALL	= heatCUDA heatCUDA_residual
all: $(ALL)

kernels.o: kernels.cu 
	$(NVCC) -c -g $(NVCCFLAGS) $+ $(LFLAGS) -o $@

heatCUDA: heatCUDA.cu kernels.o
	$(NVCC) -g -O2 $(NVCCFLAGS) $+ $(LFLAGS) -o $@

kernels_res.o: kernels_res.cu
	$(NVCC) -c -g $(NVCCFLAGS) $+ $(LFLAGS) -o $@

heatCUDA_residual: heatCUDA_res.cu kernels_res.o
	$(NVCC) -g -O2 $(NVCCFLAGS) $+ $(LFLAGS) -o $@

clean:
	rm -fr $(ALL) *.o *.prv *.pcf *.row *.sym *.mpits set-0

