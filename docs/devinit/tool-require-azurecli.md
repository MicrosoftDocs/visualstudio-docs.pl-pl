---
title: require-azurecli
description: Narzędzie devinit wymaga-azurecli.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: d73fe7c1745ded16ca6b0c94acf117c1707c1063
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440417"
---
# <a name="require-azurecli"></a>require-azurecli

`require-azurecli`Narzędzie służy do instalowania [interfejsu wiersza polecenia platformy Azure](/cli/azure/?view=azure-cli-latest&preserve-view=true) za pomocą interfejsu wiersza polecenia platformy Azure.

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                          |
| [**klawiatur**](#input)                              | ciąg | Nie       | Nie używany. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                               |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Nie używany. Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.     |

### <a name="input"></a>Dane wejściowe

Nie używany.

### <a name="additional-options"></a>Opcje dodatkowe

Nie używany.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślnym zachowaniem tego `require-azurecli` narzędzia jest zainstalowanie najnowszej wersji interfejsu wiersza polecenia platformy Azure i dodanie go do programu `PATH` .

## <a name="example-usage"></a>Przykład użycia
Poniżej znajduje się przykład sposobu uruchamiania `require-azurecli` przy użyciu `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-azure-cli"></a>.devinit.js, na którym zostanie zainstalowany interfejs wiersza polecenia platformy Azure:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azurecli"
        }
    ]
}
```