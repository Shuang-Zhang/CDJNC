# CDJNC
R package "CDJNC" for the Jacobi type CD algorithm with warmstarts in high-dimension sparse estimation, which is proposed by Jiao et al. (2020+).
# Installation

    #install.packages("devtools")
    library(devtools)
    install_github("Shuang-Zhang/CDJNC")

# Usage

   - [x] [CDJNC-manual.pdf](https://github.com/Shuang-Zhang/CDJNC/blob/master/inst/CDJNC-manual.pdf) ---------- Details of the usage of the package(haven't been uploaded yet).
# Example
    library(CDJNC)
	#Settings
	n=200
	p=1000
	K=10
	sigma=0.1
	ratio=1
	kind=1
	rho=0.1
	seed=1
	isnorm=TRUE
	#Generate data
	tic = proc.time()
	data = gdata(n, p, K, sigma, ratio, kind, rho, seed, isnorm, nnn="sqrtn", snr=1.0e-10)
	process_time = proc.time() - tic
	print("Generate data in C++ process time:")
	print(process_time)
	#CDJ algorithm
	nx = data$nx; ny = data$ny; d = data$d
	pen = "scad"; nnn = "sqrtn"; N = 100; Lmin = 1e-5; ga = 4; mu = 0.5; imax = 1; tol = 1e-5
	tic = proc.time()
	res_c = tune_cdj(nx,ny,pen,nnn,N,Lmin,ga,mu,imax,tol)
	process_time = proc.time() - tic
	print("tcdj in C++ process time:")
	print(process_time)
    
# References
Jiao Y. Coordinate Descent, Jacobi or Gauss-Siedel. Manuscript.

# Development
This R package is developed by Shuang Zhang (zhangshuang_jz@sina.cn).
