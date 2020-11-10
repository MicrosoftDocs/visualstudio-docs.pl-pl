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
ms.openlocfilehash: 1f66f691bd92c6cc9d315c58225b9345198fe96d
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435767"
---
# <a name="getting-started-with-devinit"></a>Wprowadzenie z devinit

devinit to narzędzie, którego można użyć, aby umożliwić każdemu użytkownikowi uzyskanie kodu i wydajną pracę w repozytorium, uruchamiając proste polecenie. Za pomocą devinit można definiować wszystkie zależności w całym systemie, które wymagają repozytorium, takie jak SQL Server, Node.js, Docker lub IIS. Devinit może wywoływać innych narzędzi i menedżerów pakietów, aby zainstalować elementy wymagane przez repozytorium. Można zdefiniować te zależności w pliku JSON o nazwie [.devinit.jsna](devinit-json.md) , a następnie następna osoba, która ma korzystać z repozytorium, wystarczy uruchomić [`devinit init`](devinit-commands.md#init) w celu zainstalowania wszystkich tych zależności. W związku z tym zamiast spędzać półroczne dołączenie do nowego repozytorium, można to zrobić w ciągu kilku minut.

devinit nie jest menedżerem pakietów ani narzędziem konfiguracji maszyny wirtualnej (VM) w obu tych wersjach. Jest to moduł uruchamiający zadania dla pliku manifestu o nazwie [.devinit.json](devinit-json.md), który definiuje zależności całego systemu wymagane przez aplikację. Aby zainstalować te zależności, devinit korzysta z narzędzi, które mogą już być używane, takich jak [czekolady](https://chocolatey.org). Dostępne narzędzia znajdują się na [pełnej liście](devinit-tool-list.md). Korzystanie z tych narzędzi zamiast bezpośredniego dystrybuowania oprogramowania devinit zapewnia wygodę korzystania z wybranego narzędzia i umożliwia korzystanie z istniejących konfiguracji, na przykład pliku [packages.config](https://chocolatey.org/docs/commands-install#packagesconfig) dla czekolady.  

## <a name="step-1-get-devinit"></a>Krok 1. Pobieranie devinit

devinit jest obecnie dostępna tylko w ramach usługi GitHub Codespaces w przypadku korzystania z programu Visual Studio i jest dostępny z poziomu zintegrowanego terminalu w programie Visual Studio. W przyszłości devinit będzie dostępny w ramach programu Visual Studio.

## <a name="step-2-define-your-environment"></a>Krok 2. Definiowanie środowiska

Najważniejszym krokiem jest zdefiniowanie środowiska deweloperskiego w [.devinit.jspliku](devinit-json.md). Ten plik będzie używany przez devinit do tworzenia środowiska podczas uruchamiania `devinit init` .

Na potrzeby tego kroku zapoznaj się z instrukcjami podanymi przez kogoś, kto może zacząć korzystać z repozytorium projektu. Czy na przykład należy zainstalować program SQL? Określona wersja platformy .NET Core? I tak dalej. Następnie dla każdej z tych zależności poszukaj odpowiedniego narzędzia devinit na [liście narzędzi](devinit-tool-list.md) i Dodaj je do `.devinit.json` pliku repozytorium. Możesz również zobaczyć wybrane przykłady w [dokumentacji przykładów](sample-readme.md).

## <a name="step-3-enjoy"></a>Krok 3. Ciesz się!

Teraz wszyscy osoby trzeba wykonać, gdy zostanie uruchomione klonowanie repozytorium `devinit init` .

```console
devinit init
```

Jeśli korzystasz z usługi [GitHub Codespaces](https://github.com/features/codespaces), możesz skonfigurować program `devinit init` do uruchamiania automatycznie po zainicjowaniu obsługi administracyjnej codespace. Aby dowiedzieć się więcej, zapoznaj się z [dokumentacją devinit i serwisem GitHub Codespaces](devinit-and-codespaces.md).
