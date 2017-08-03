* ```$caffe_root/build/tools/caffe.bin``` 由 ```$caffe_root/tools/caffe.cpp```编译而来
* ```$caffe_root/tools/caffe.cpp```中的核心调用栈为
	* ```main ---> GetBrewFunction(caffe::string(argv[1]))()```，返回4种命令——train test time device_query 的其中之一
	* train函数中
		* ```
	caffe::SolverParameter solver_param;
	caffe::ReadSolverParamsFromTextFileOrDie(FLAGS_solver, &solver_param);
	//将solver.prototxt中的参数解析到SolverParameter类中
	```
		* ```
	shared_ptr<caffe::Solver<float> >
      solver(caffe::SolverRegistry<float>::CreateSolver(solver_param));//这行代码基本上完成了所有的初始化工作
      ```
      	* 网络求解 solver->Solve()
      * ```$caffe_root/src/caffe/solvers/sgd_solver.cpp``` 中 ```REGISTER_SOLVER_CLASS(SGD);```
      * ```$caffe_root/src/caffe/solvers/sgd_solver.cpp``` 中 ```REGISTER_SOLVER_CLASS(SGD);```
      * ```template <typename Dtype> void Net<Dtype>::Init(const NetParameter& in_param)``` 中一个大大的for循环来设置各个层
      * ``` Net<Dtype>::Net(const NetParameter& param) {
  		Init(param);//Net中初始化了各个层
	}
	```
	*```$caffe_root/tools/caffe.cpp```中train函数中
	``` solver->Solve();```进行网络求解
	
	
	
	

      