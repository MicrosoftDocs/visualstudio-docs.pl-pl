---
title: require-azureartifactscredentialprovider
description: Narzędzie devinit wymaga-azureartifactscredentialprovider.
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
ms.openlocfilehash: ad39bc070841dae5202abca8ca4624927a100f23
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440389"
---
# <a name="require-azureartifactscredentialprovider"></a>require-azureartifactscredentialprovider

`require-azureartifactscredentialprovider`Narzędzie instaluje Azure Artifacts dostawcy poświadczeń. Dostawca poświadczeń Azure Artifacts automatyzuje pozyskiwanie poświadczeń wymaganych do przywrócenia pakietów NuGet w ramach przepływu pracy deweloperskiej platformy .NET. Więcej informacji na temat Azure Artifacts dostawcy poświadczeń można znaleźć [tutaj](https://github.com/microsoft/artifacts-credprovider/blob/master/README.md).

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                                |
| [**klawiatur**](#input)                              | ciąg | Nie       | Nie używany. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) . |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.                     |

### <a name="input"></a>Dane wejściowe

Nie używany. Ignoruje wszelkie dane wejściowe, jeśli są wymienione.

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje są przesyłane jako-do polecenia dostawcy poświadczeń.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślnym zachowaniem tego `require-azureartifactscredentialprovider` narzędzia jest zainstalowanie najnowszej wersji dostawcy poświadczeń Azure Artifacts.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajduje się przykład sposobu uruchamiania `require-azureartifactscredentialprovider` przy użyciu `.devinit.json` .

#### <a name="devinitjson-that-will-install-azure-artifacts-credential-provider"></a>.devinit.js, na którym zostanie zainstalowany dostawca poświadczeń Azure Artifacts:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
        }
    ]
}
```
