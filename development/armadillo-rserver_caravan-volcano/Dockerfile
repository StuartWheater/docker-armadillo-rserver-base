FROM datashield/armadillo-rserver_caravan:1.1.0

# Update package metdata
RUN apt-get update -y

# Install OS dependencies
RUN apt-get install liblzma-dev libicu-dev -y

# Install dsBase development package
ENV DSBASE_BRANCH "6.2.0"
RUN installGithub.r "datashield/dsBase@${DSBASE_BRANCH}" --deps TRUE

# Install dsMediation development package
ENV DSMEDIATION_BRANCH "0.0.3"
RUN installGithub.r "datashield/dsMediation@${DSMEDIATION_BRANCH}" --deps TRUE

# Install dsBayesPathAnalysis development package
ENV DSBAYESPATHANALYSIS_BRANCH "main"
RUN installGithub.r "StuartWheater/dsBayesPathAnalysis@${DSBAYESPATHANALYSIS_BRANCH}" --deps TRUE

# Install BioConductor package
RUN installBioc.r 'Biobase'
RUN installBioc.r 'rexposome'

# Install dsExposome development package
ENV DSEXPOSOME_BRANCH "2.0.4"
RUN installGithub.r "isglobal-brge/dsExposome@${DSEXPOSOME_BRANCH}" --deps TRUE

# Setup entry point to MolgenisRServer::Rserve
CMD R -e "MolgenisRserve::Rserve(debug=${DEBUG}, args='--vanilla --RS-set remote=enable --RS-set auth=disable --RS-set daemon=disable')"
