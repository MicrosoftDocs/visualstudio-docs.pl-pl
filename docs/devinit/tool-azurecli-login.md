---
title: azurecli-login
description: devinit narzędzia azurecli — logowanie.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: eb83c6a1a2944518fbfa541b03bc14f701f164dc
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862273"
---
# <a name="azurecli-login"></a>azurecli-login

`azurecli-login`Narzędzie służy do logowania się do Azure Active Directory za pomocą [interfejsu wiersza polecenia platformy Azure](/cli/azure/authenticate-azure-cli?preserve-view=true&view=azure-cli-latest). To narzędzie korzysta z wiersza polecenia platformy Azure: `az login --use-device-code` Aby ukończyć logowanie, należy postępować zgodnie z instrukcjami wydrukowanymi w konsoli programu.

## <a name="usage"></a>Użycie

Jeśli obie właściwości zostały pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

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

Domyślnym zachowaniem tego `azurecli-login` narzędzia jest zainstalowanie najnowszej wersji interfejsu wiersza polecenia platformy Azure i dodanie jej do ścieżki (tylko system Windows).

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger az login --use-device-code behavior.",
            "tool": "azurecli-login"
        }
    ]
}
```