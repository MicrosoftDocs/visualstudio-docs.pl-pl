---
title: azurecli-login
description: devinit narzędzia azurecli — logowanie.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 64b215912c21a405c2b2c3a0feb3720a4ab16c44
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671666"
---
# <a name="azurecli-login"></a>azurecli-login

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

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

Domyślnym zachowaniem tego `azurecli-login` narzędzia jest zainstalowanie najnowszej wersji interfejsu wiersza polecenia platformy Azure i dodanie go do programu `PATH` .

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