## Discussion ##

* initiation to docker and main commands, 
* example to run dockerized tools in snakemake rules, 

## Example

Download dataset from tophat2 tutoriel : (https://ccb.jhu.edu/software/tophat/downloads/test_data.tar.gz)

Example on __Snakefile__ with [docker](https://www.docker.io/) 

```vim
rule quality:
    input:
        "reads_2.fq"
    shell:
        "docker run -v /root/mydisk/snakemake/test_data:/data -w /data docker-registry.genouest.org/ifb/fastqc:0.11.5 fastqc {input}"

rule docker_h:
    input:
        "reads_2.fq"
    shell:
        "docker run -v /root/mydisk/snakemake/test_data:/data -w /data docker-registry.genouest.org/ifb/tophat:2.1.0 tophat -p 20 test_ref {input}"
