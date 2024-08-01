# typescript で Jest を使うための準備

## Typescript の準備

### typescript のインストール

```bash
npm install --save-dev typescript ts-node
```

### typescript の設定ファイル作成

```bash
npx tsc --init
```

リポジトリ内の tsconfig.json は自動生成したファイルからコメント部分を削除して見やすくしたもので、
設定自体は初期の状態となってます。

## Jest インストール

### Jest インストール

```bash
npm install --save-dev jest @types/jest @jest/globals ts-jest
```

### jest の設定ファイルの作成

```bash
npx ts-jest config:init
```

## コードの準備

テスト対象のコードの add 関数を作成します。

```ts
// srcs/calc.ts
export function add(a: number, b: number): number {
  return a + b;
}
```

テストコードを作成します

```ts
// srcs/calc.test.ts
import { describe, expect, test } from "@jest/globals";
import { add } from "./calc";

describe("sum function", () => {
  test("adds 1+2 to equal 3", () => {
    expect(add(1, 2)).toBe(3);
  });
});
```

## テスト実行

package.json の script 部分を修正して jest が実行されるようにします。

```json
"scripts": {
	"test": "jest"
},
```

以下のコマンドでテストが実行されます。

```bash
npm test
```

# 参考

- [公式 - はじめましょう](https://jestjs.io/ja/docs/getting-started)
