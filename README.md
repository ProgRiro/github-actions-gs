# github-actions-gs

## ♻️ work flow

- strategy: matrix: を用いて、nodeのバージョン複数でのテストを実行するようにした
- needs: を用いて、依存関係を作成。配列とすることで、複数のジョブが終了した後に最後のジョブが実行されるようにした
- actions/upload-artifact@v1 を用いて、ファイルを書き出すようにした。ここで書き出したファイルは、他のジョブで参照できる
- actions/download-artifact@v2 を用いて、上で書き出したファイルを読み込むようにした

## 📝 memo

- workflowは並列で実行されるため、依存関係を持たせたい場合は、同じworkflow内で複数のジョブを定義し、needsで依存関係を持たせて実行するようにする
- actions/upload-artifact@v1 でファイルを書き出せる
- actions/download-artifact@v2 で書き出したファイルを読み込める
- ジョブ内には、必ずruns-onが必要
- ジョブ内の処理はstep内に記述する（usesやrun）
- 複数のバージョンでテストしたい場合は、strategy: matrix: を用いる
