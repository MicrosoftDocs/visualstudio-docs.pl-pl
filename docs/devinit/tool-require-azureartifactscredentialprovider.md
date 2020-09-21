---
title: Wymagaj — azureartifactscredentialprovider
description: Narzędzie devinit wymaga-azureartifactscredentialprovider.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 74e8775fb9dc864e8026f73e3bc75604dbf32e10
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810913"
---
# <a name="require-azureartifactscredentialprovider"></a>Wymagaj — azureartifactscredentialprovider

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

Domyślnym zachowaniem tego `require-azureartifactscredentialprovider` narzędzia jest zainstalowanie najnowszej wersji Azure Artifacts dostawcy poświadczeń.

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that installs Azure Artifacts Credential Provider.'",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
            "comments": "Installs Azure Artifacts Credential Provider."
        }
    ]
}
```
