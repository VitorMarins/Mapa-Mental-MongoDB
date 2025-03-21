# Mapa Mental dos Comandos do MongoDB

## 1. **Criação e Estrutura de Coleções**
- **`db.createCollection()`**: Cria uma nova coleção.
  - Exemplo: `db.createCollection("minhaColecao")`
- **`db.collection.renameCollection()`**: Renomeia uma coleção.
  - Exemplo: `db.minhaColecao.renameCollection("novaColecao")`
- **`db.collection.drop()`**: Remove uma coleção.
  - Exemplo: `db.minhaColecao.drop()`

## 2. **Operações de Inserção**
- **`db.collection.insertOne()`**: Insere um único documento em uma coleção.
  - Exemplo: `db.minhaColecao.insertOne({ nome: "João", idade: 30 })`
- **`db.collection.insertMany()`**: Insere múltiplos documentos em uma coleção.
  - Exemplo: `db.minhaColecao.insertMany([{ nome: "Maria", idade: 25 }, { nome: "Pedro", idade: 35 }])`
- **`db.collection.save()`**: Insere um documento ou atualiza se já existir.
  - Exemplo: `db.minhaColecao.save({ _id: 1, nome: "Carlos", idade: 40 })`

## 3. **Operações de Leitura**
- **`db.collection.find()`**: Retorna todos os documentos que correspondem a uma consulta.
  - Exemplo: `db.minhaColecao.find({ idade: { $gt: 20 } })`
- **`db.collection.findOne()`**: Retorna um único documento.
  - Exemplo: `db.minhaColecao.findOne({ nome: "João" })`
- **`db.collection.distinct()`**: Retorna um array de valores distintos para um campo.
  - Exemplo: `db.minhaColecao.distinct("nome")`
- **`db.collection.aggregate()`**: Processa dados e retorna resultados agregados.
  - Exemplo: `db.minhaColecao.aggregate([{ $match: { idade: { $gt: 20 } } }, { $group: { _id: "$status", total: { $sum: 1 } } }])`
- **`db.collection.countDocuments()`**: Conta o número de documentos correspondentes a uma consulta.
  - Exemplo: `db.minhaColecao.countDocuments({ idade: { $gt: 20 } })`
- **`db.collection.explain()`**: Explica como a operação será executada.
  - Exemplo: `db.minhaColecao.find({ idade: { $gt: 20 } }).explain("executionStats")`

## 4. **Operações de Atualização**
- **`db.collection.updateOne()`**: Atualiza um único documento.
  - Exemplo: `db.minhaColecao.updateOne({ nome: "João" }, { $set: { idade: 31 } })`
- **`db.collection.updateMany()`**: Atualiza múltiplos documentos.
  - Exemplo: `db.minhaColecao.updateMany({ idade: { $lt: 30 } }, { $set: { status: "jovem" } })`
- **`db.collection.replaceOne()`**: Substitui um único documento.
  - Exemplo: `db.minhaColecao.replaceOne({ nome: "Ana" }, { nome: "Ana", idade: 29, cidade: "São Paulo" })`
- **`db.collection.findOneAndUpdate()`**: Encontra e atualiza um documento.
  - Exemplo: `db.minhaColecao.findOneAndUpdate({ nome: "Carlos" }, { $set: { idade: 41 } })`

## 5. **Operações de Exclusão**
- **`db.collection.deleteOne()`**: Remove um único documento.
  - Exemplo: `db.minhaColecao.deleteOne({ nome: "Pedro" })`
- **`db.collection.deleteMany()`**: Remove múltiplos documentos.
  - Exemplo: `db.minhaColecao.deleteMany({ idade: { $gt: 30 } })`
- **`db.collection.findOneAndDelete()`**: Encontra e deleta um documento.
  - Exemplo: `db.minhaColecao.findOneAndDelete({ nome: "Carlos" })`

## 6. **Operações de Indexação**
- **`db.collection.createIndex()`**: Cria um índice.
  - Exemplo: `db.minhaColecao.createIndex({ nome: 1 })`
- **`db.collection.dropIndex()`**: Remove um índice específico.
  - Exemplo: `db.minhaColecao.dropIndex("nome_1")`
- **`db.collection.getIndexes()`**: Retorna uma lista de índices.
  - Exemplo: `db.minhaColecao.getIndexes()`
- **`db.collection.dropIndexes()`**: Remove todos os índices.
  - Exemplo: `db.minhaColecao.dropIndexes()`
- **`db.collection.reIndex()`**: Recria todos os índices.
  - Exemplo: `db.minhaColecao.reIndex()`

## 7. **Operações de Agregação e MapReduce**
- **`db.collection.mapReduce()`**: Processa documentos e retorna resultados agregados.
  - Exemplo: `db.minhaColecao.mapReduce(function() { emit(this.nome, 1) }, function(key, values) { return Array.sum(values) }, { out: "resultadoMapReduce" })`

## 8. **Operações de Monitoramento**
- **`db.collection.watch()`**: Escuta mudanças em uma coleção.
  - Exemplo: `const changeStream = db.minhaColecao.watch(); changeStream.on("change", (change) => console.log(change))`
- **`db.collection.stats()`**: Retorna estatísticas sobre a coleção.
  - Exemplo: `db.minhaColecao.stats()`
- **`db.collection.validate()`**: Valida a integridade de uma coleção.
  - Exemplo: `db.minhaColecao.validate()`

## 9. **Operações de Tamanho e Armazenamento**
- **`db.collection.dataSize()`**: Retorna o tamanho dos dados da coleção.
  - Exemplo: `db.minhaColecao.dataSize()`
- **`db.collection.totalSize()`**: Retorna o tamanho total da coleção (incluindo índices).
  - Exemplo: `db.minhaColecao.totalSize()`
- **`db.collection.storageSize()`**: Retorna o tamanho de armazenamento da coleção.
  - Exemplo: `db.minhaColecao.storageSize()`
- **`db.collection.totalIndexSize()`**: Retorna o tamanho total dos índices.
  - Exemplo: `db.minhaColecao.totalIndexSize()`

## 10. **Operações Diversas**
- **`db.collection.convertToCapped()`**: Converte uma coleção para uma coleção limitada (capped).
  - Exemplo: `db.minhaColecao.convertToCapped(1024)`
- **`db.collection.bulkWrite()`**: Executa operações de escrita em massa.
  - Exemplo: `db.minhaColecao.bulkWrite([{ insertOne: { document: { nome: "Ana", idade: 28 } } }, { updateOne: { filter: { nome: "João" }, update: { $set: { idade: 32 } } } }])`
