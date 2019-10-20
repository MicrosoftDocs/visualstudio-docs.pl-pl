---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, społeczność Dotfuscator, z przetworami, rozwiązania do zastępujące, ochrona przed zami, ochrona, Edycja, wersja Community, mieszanie, .NET, bezpłatnie, Visual Studio 2019, Visual Studio 2017, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: Dowiedz się, jak chronić swoje aplikacje .NET za pomocą bezpłatnej kopii społeczności Dotfuscator zawartej w programie Visual Studio.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18e2ee678e5cf71693d12d4ddeb6af51f55a870b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652425"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

***Ochrona przed zmianami — Dotfuscator*** zapewnia kompleksową ochronę aplikacji platformy .NET, która jest łatwa w obsłużyniu bezpiecznego cyklu tworzenia oprogramowania.
Umożliwia ona zabezpieczanie, ochronę i oczyszczanie aplikacji klasycznych, mobilnych, serwerowych i osadzonych w celu zapewnienia bezpieczeństwa tajemnic handlowych i innej własności intelektualnej, zmniejszenie piractwa i fałszowanie oraz ochronę przed manipulacjami i nieautoryzowanymi debugowaniem.
Dotfuscator działa na skompilowanych zestawach bez konieczności dodatkowego programowania, a nawet uzyskiwania dostępu do kodu źródłowego.

![Ochrona przed przewagęm — Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Dlaczego ochrona

Ważne jest, aby **chronić własność intelektualną** (IP).
Kod aplikacji zawiera szczegółowe informacje o projekcie i implementacji, które mogą być uznawane za adres IP.
Jednak aplikacje skompilowane na .NET Framework [zawierają znaczące metadane i kod pośredni wysokiego poziomu][assemblies], dzięki czemu można je łatwo odtworzyć, a tylko przy użyciu jednego z wielu bezpłatnych, zautomatyzowanych narzędzi.
Zakłócając i zatrzymując odwracanie, można zapobiec nieautoryzowanemu ujawnianiu adresów IP, a także udowodnić, że Twój kod zawiera tajemnice handlowe.
Dotfuscator może [zasłaniać][obfuscation] zestawy .NET, aby utrudnić odtwarzanie na odwrót, zachowując oryginalne zachowanie aplikacji.

Ważne jest również, aby **chronić integralność aplikacji**.
Niemniej poza odtwarzaniem, nieszkodliwe osoby mogą próbować zapirackie działanie aplikacji, zmienić zachowanie aplikacji w czasie wykonywania lub manipulować danymi.
Dotfuscator może wstrzyknąć aplikację, umożliwiając [wykrywanie i reagowanie na nieautoryzowane użycie][checks], w tym manipulowanie, debugowanie innych firm i urządzenia z odblokowanym dostępem.

Aby uzyskać więcej informacji na temat sposobu, w jaki Dotfuscator mieści się w całym cyklu tworzenia oprogramowania, zobacz [stronę ochrony aplikacji SDL][sdl-protection]z rozwiązaniami

## <a name="about-dotfuscator-community"></a>Społeczność Dotfuscator — informacje

Twoja kopia Microsoft Visual Studio obejmuje kopię ***Dotfuscator Community Protection***, bezpłatnie do użytku osobistego.
(Ta bezpłatna wersja była wcześniej znana jako Dotfuscator Community Edition lub Dotfuscator CE). Aby uzyskać instrukcje dotyczące sposobu instalowania wersji Dotfuscator Community dołączonej do programu Visual Studio, zobacz [stronę instalacji][install].

Społeczność Dotfuscator oferuje szereg usług [ochrony oprogramowania i ograniczania funkcjonalności][software-protection] dla deweloperów, architektów i testerów.
Przykłady zaciemnienia [platformy .NET][obfuscation] i inne funkcje [ochrony aplikacji][app-protection] zawarte w Dotfuscator Community to:

* *[Zmiana nazw][renaming]* identyfikatorów w celu łatwiejszego odtworzenia skompilowanych zestawów.
* *[Ochrona przed fałszowaniem][tamper]* w celu wykrywania wykonywania naruszonych aplikacji oraz kończenia lub reagowania na naruszone sesje.
* *[Program chroniący przed debugowaniem][debug]* , który wykrywa dołączenie debugera do uruchomionej aplikacji i kończy lub reaguje na debugowane sesje.
* *[Urządzenie z certyfikatem][root]* z systemem, aby wykryć, czy aplikacja jest uruchomiona na urządzeniu z systemem Android, i zakończyć lub odpowiedzieć na sesje na tych urządzeniach.
* *[Zachowania wygasania aplikacji][shelflife]* , które kodują datę "koniec okresu istnienia" i przerywają wygasłe sesje aplikacji.

Aby uzyskać szczegółowe informacje dotyczące tych funkcji, w tym ich dopasowania do strategii ochrony aplikacji, zobacz [stronę możliwości][capabilities].

Społeczność Dotfuscator oferuje podstawową ochronę.
Jeszcze więcej miar ochrony aplikacji jest dostępnych dla zarejestrowanych użytkowników społeczności Dotfuscator oraz do użytkowników z prawami do przeprowadzenia ***ochrony Dotfuscator Professional***, wiodącego na świecie [środowiska platformy .NET][net-obfuscator].
Informacje o ulepszaniu Dotfuscator można znaleźć na [stronie uaktualnienia][upgrades].

## <a name="getting-started"></a>Wprowadzenie

::: moniker range="vs-2019"

Aby rozpocząć korzystanie z społeczności Dotfuscator z poziomu programu Visual Studio, wpisz `dotfuscator` w **polu wyszukiwania** (Ctrl + Q).

* Jeśli społeczność Dotfuscator jest już zainstalowana, w **polu wyszukiwania** zostanie wyświetlona opcja rozpoczęcia Dotfuscator Community w nagłówku *menu* . Aby uzyskać szczegółowe informacje, zobacz [stronę wprowadzenie podręcznika użytkownika Dotfuscator][get-started].
* Jeśli społeczność Dotfuscator nie jest jeszcze zainstalowana, w **polu wyszukiwania** będzie wyświetlana wartość **Zainstaluj ponownie ochronę Dotfuscator** w ramach nagłówka *poszczególne składniki* . Aby uzyskać szczegółowe informacje, zobacz [stronę instalacji][install] .

::: moniker-end

::: moniker range="vs-2017"

Aby rozpocząć korzystanie z społeczności Dotfuscator z poziomu programu Visual Studio, wpisz `dotfuscator` na pasku wyszukiwania **szybkiego uruchamiania** (Ctrl + Q).

* Jeśli społeczność Dotfuscator jest już zainstalowana, **Szybkie uruchamianie** powoduje wyświetlenie opcji *menu* , aby uruchomić interfejs użytkownika społeczności Dotfuscator. Aby uzyskać szczegółowe informacje, zobacz [stronę wprowadzenie podręcznika użytkownika Dotfuscator][get-started].
* Jeśli społeczność Dotfuscator nie jest jeszcze zainstalowana, **Szybkie uruchamianie** powoduje wyświetlenie odpowiedniej opcji *instalacji* . Aby uzyskać szczegółowe informacje, zobacz [stronę instalacji][install] .

::: moniker-end

**Najnowszą wersję** społeczności Dotfuscator można także uzyskać ze [strony plików do pobrania Dotfuscator na PreEmptive.com][download].

## <a name="full-documentation"></a>Pełna dokumentacja

Ta strona i jej podstrony zapewniają ogólne omówienie funkcji społeczności Dotfuscator oraz [instrukcje dotyczące instalowania narzędzia][install].

Aby uzyskać szczegółowe [instrukcje dotyczące użycia][get-started], zobacz [Dotfuscator Podręcznik użytkownika społeczności w witrynie PreEmptive.com][full] .

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html
