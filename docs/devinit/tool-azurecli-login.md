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
ms.openlocfilehash: 304c7b12e3b290c3e47857877b050b18873e3934
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672312"
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
Poniżej znajduje się przykład sposobu uruchamiania `azurecli-login` przy użyciu `.devinit.json` . 

#### <a name="devinitjson-that-will-trigger-azure-login"></a>.devinit.js, na którym zostanie wyzwolone logowanie na platformie Azure:

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "azurecli-login"
        }
    ]
}
```