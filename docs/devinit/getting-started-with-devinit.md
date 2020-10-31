---
title: Wprowadzenie z devinit
description: Wprowadzenie do przewodnika dla devinit.
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
ms.openlocfilehash: ae274e460f4404efa92c4cf3785a3c2e41fd9691
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134078"
---
# <a name="getting-started-with-devinit"></a>Wprowadzenie z devinit

## <a name="step-1-get-devinit"></a>Krok 1. Pobieranie devinit

devinit jest obecnie dostępna tylko w ramach usługi GitHub Codespaces w przypadku korzystania z programu Visual Studio i jest dostępny z poziomu zintegrowanego terminalu w programie Visual Studio. W przyszłości devinit będzie dostępny w ramach programu Visual Studio.

## <a name="step-2-define-your-environment"></a>Krok 2. Definiowanie środowiska

Najważniejszym krokiem jest zdefiniowanie środowiska deweloperskiego w [ _.devinit.js_ pliku](devinit-json.md). Ten plik będzie używany przez devinit do tworzenia środowiska podczas uruchamiania `devinit init` .

Na potrzeby tego kroku zapoznaj się z instrukcjami podanymi przez kogoś, kto może zacząć korzystać z repozytorium projektu. Czy na przykład należy zainstalować program SQL? Określona wersja platformy .NET Core? itd. Następnie dla każdej z tych zależności poszukaj odpowiedniego narzędzia devinit na [liście narzędzi](devinit-tool-list.md) i Dodaj je do _.devinit.jsrepozytorium na_ pliku.

## <a name="step-3-enjoy"></a>Krok 3. Ciesz się!

Teraz wszyscy osoby trzeba wykonać, gdy zostanie uruchomione klonowanie repozytorium `devinit init` .

```console
devinit init
```

Jeśli korzystasz z usługi [GitHub Codespaces](https://github.com/features/codespaces), możesz skonfigurować program `devinit init` do uruchamiania automatycznie po zainicjowaniu obsługi administracyjnej codespace. Aby dowiedzieć się więcej, zobacz [dokumentację dotyczącą usługi devinit i serwisu GitHub Codespaces](devinit-and-codespaces.md).
