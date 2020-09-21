---
title: Wprowadzenie z devinit
description: Wprowadzenie do przewodnika dla devinit.
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
ms.openlocfilehash: e0c6676b65637840a1b5878e06d6c5861c34e65d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809314"
---
# <a name="getting-started-with-devinit"></a>Wprowadzenie z devinit

## <a name="step-1-get-devinit"></a>Krok 1. Pobieranie devinit

devinit jest obecnie dostępna tylko w ramach usługi GitHub Codespaces w przypadku korzystania z programu Visual Studio i jest dostępny z poziomu zintegrowanego terminalu w programie Visual Studio. W przyszłości devinit będzie dostępny w ramach programu Visual Studio.

## <a name="step-2-define-your-environment"></a>Krok 2. Definiowanie środowiska

Najważniejszym krokiem jest zdefiniowanie środowiska deweloperskiego w [ _.devinit.js_ pliku](devinit-json.md). Ten plik będzie używany przez devinit do tworzenia środowiska podczas uruchamiania `devinit init` .

Na potrzeby tego kroku zapoznaj się z instrukcjami podanymi przez kogoś, kto może zacząć korzystać z repozytorium projektu. Czy na przykład należy zainstalować program SQL? Określona wersja platformy .NET Core? itd. Następnie dla każdej z tych zależności poszukaj odpowiedniego narzędzia devinit na [liście narzędzi](devinit-tool-list.md)) i Dodaj je do _.devinit.jsrepozytorium na_ pliku.

## <a name="step-3-enjoy"></a>Krok 3. Ciesz się!

Teraz wszyscy osoby trzeba wykonać, gdy zostanie uruchomione klonowanie repozytorium `devinit init` .

```batch
> devinit init
```

Jeśli korzystasz z usługi [GitHub Codespaces](https://github.com/features/codespaces), możesz skonfigurować program `devinit init` do uruchamiania automatycznie po zainicjowaniu obsługi administracyjnej codespace. Aby dowiedzieć się więcej, zobacz [dokumentację dotyczącą usługi devinit i serwisu GitHub Codespaces](devinit-and-codespaces.md).
