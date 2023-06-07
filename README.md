# ml-msto
Machine learning-based multiscale topology optimization

By: Joel Najmon and Andres Tovar

This is a MATLAB code repository for the machine learning-based multiscale topology optimization (ML-MSTO) method proposed in the 2023 journal paper: "Multiscale Topology Optimization via Artificial Neural Netowrks and Displacement-driven Toplogy-optimized Microstructures" submitted to Structural and Multidisciplinary Optimization (SMO) in June 2023. The paper is currently under review.

Below are instructions on how to run reduced fidelity versions of the 2D and 3D examples found in the submitted manuscript.
Only lines 7-23 of the MAIN_v3_0_ML_MSTO_Optimizer.m file need to be modified to run the examples.

2D Cantilever Beam (density-graded design case):
macro.nelx = 60;
macro.nely = 30;
macro.nelz = 0; if macro.nelz == 0; macro.dim = 2; else; macro.dim = 3; end % set to 0 if 2D
macro.volfrac = 0.50;
macro.cont = 0; % Continuation: 1 = Yes, 0 = No (Untested)
macro.flt_den_min = 1.0; %     density filter minimum radius (flt_den_min <= 1 is off)
macro.flt_sen_min = 3.0; % sensitivity filter minimum radius (flt_sen_min <= 1 is off)
macro.delta = 0.9; % Maximum allowable limit in density between adjacent macroscale elements. [0 1] (1 = no constraint), (0 = fixed design)
macro.x_lb(1) = 0; macro.x_ub(1) = 1; % bounds for the density design
macro.x_lb(2) = 0; macro.x_ub(2) = 1; % bounds for the weight design
macro.h_fd = 0; % SA via ANN: h_fd = 0; SA via CFD: h_fd = [0.001, 0.001] (pertubation size for density and weight design variables)
macro.vf_cutoff = 0.1; % cutoff volume fraction for CH interpolation

macro.alg = 3; % alg=1: fmincon, alg=2: OC, alg=3: GOC, alg=4: MMA
macro.maxloop = 5;   % Maximum number of iterations
macro.tolx = 1e-3;    % Termination criterion
macro.displayflag = 1; % Display structure actively flag
