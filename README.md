15.12.2023: Carico file main_rat, hip_models e Fig2_mod

N.B.! Nel main si lanciano gli altri due script che generano output e figure. 
      Sul main va cambiata la main_path che è a directory dove vogliamo mettere tutto
      e nella quale verrà contestualmente creata una cartella "images" in cui compaiono 
      tutte le figure (carico anche quella cartella in cui ho messo già le figure generate
      con 4000, 5000 e 10000 iterazioni). Contestualmente si generano anche gli output in formato
      .mat per fare grafici ed elaborazioni su Matlab.
      Inoltre, la cartella figure ottenute contiene vecchie figure (ci sono anche quelle fatte sui dati EEG di Mirco in prima battuta). 
      La cartella MatLab_files contiene tutti gli script per generare i grafici più il principale, cebra_script che fa partire tutto su MatLab (in Lavorazione).
      La cartella Third_Party contien script per altri algoritmi (nello specifico pi_vae che va raffinato). 

      main path è anche argomento (input) dei due script (quindi va cambiata SOLO sul main). 
      Se vogliamo generare gli output a livello intermedio, basta andare nella parte del main

      if __name__=="__main__":
        main() 
     
     e cambiarla in 

     if __name__=="__main__":
      dd, err_loss, mod_pred= main()


19.12.2023: Carico file wrap_ML e wrap_py per output per elaborazioni direttamente da MatLab



Thur, 27.03.24. Upload tsne and umap fit and trasform (.py files) and parameter definition (both for fit and transform .mat files)

FIT files are made up of 5 functions: 

- load_data(input_dir, data_filename='default') filename can be changed of course; just 
  notice that we always point to 'rat_n' in the .mat files. We should make this more general, starting from the split/join in trials file.

- load_params(input directory, params_filename);Assume the params file always has the     
  same structure we provide from MATLAB.

- configure_and_fit_method(data, params) function taking as input the data and params 
  previously loaded and defining the model (i.e. calling the -hyper-paramas from the param file); note that params can be added to the list; actually I hve already included the most frequently used for both methods 

- save_embedding(embedding_output, output_dirctory, filename ='model_embedding.mat')
  (the name is a default one; it can be changed). This function is optional so is not passing in the baseline context

- save_model(model, output_dir, model_name=method_model.pkl)

  The main call wants the script_name, output and input directory, the data_file, the param_  file (both in .mat format)


TRANSFORM files are  made up of two functions:

- load_model(model_file, data): this function load from the directories we pass from the  
  the data to trasnform dn the model we got from the fit files

- transform_data(model, data_mat): this functios takes as inputs the model loaded with the previous function and the data file which is a .mat with a 'data_n' fieldname (check)

- The main call wants the script name, the model_file (.pkl) both output and input 
  directory

  Sun, 31.03.24. Upload tsne and umap main and miscellanea to run them on matlab. Check parameters spec and correct settings