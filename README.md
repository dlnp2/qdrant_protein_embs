# Playing with Qdrant and ProtT5 embeddings
[Qdrant](https://qdrant.tech/) is a vector database implemented in Rust for robust and scalable nearest neighbour search. In this playground, we take a look into the technology by registering and searching protein embeddings pre-calculated using [ProtT5](https://github.com/agemagician/ProtTrans) published on UniProt.

## Developmental environment
- Ubuntu 18.04.6 LTS (Bionic Beaver)
- Docker version 24.0.2, build cb74dfc
- Python 3.10.11
- Qdrant server image v1.2.2
- Data downloaded from UniProt as of 2023.06.01

## Data
Download data from [the FTP site](https://ftp.uniprot.org/pub/databases/uniprot/current_release/knowledgebase/embeddings/). Specifically, we use Homo sapiens data (UP000005640_9606).

## How to use Qdrant via Python API
1. Start Qdrant server:
    ```shell
    docker run -p 6333:6333 \
        -v $(pwd)/qdrant_storage:/qdrant/storage \
        qdrant/qdrant:v1.2.2
    ```
2. Create a client:
    ```python
    from qdrant_client import QdrantClient
    client = QdrantClient(host="localhost", port=6333, grpc_port=6334)
    # do interesting stuffs
    ```