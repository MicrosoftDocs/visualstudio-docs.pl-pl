---
title: Omówienie usługi GitHub Codespaces (wersja zapoznawcza)
description: Dowiedz się więcej o usłudze GitHub Codespaces z programem Visual Studio oraz o tym, jak można zwiększyć środowisko programistyczne w chmurze.
ms.topic: overview
ms.date: 09/04/2020
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: a0991fa1760e2ea4592ec861f9d2d29a5763eaea
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90862190"
---
# <a name="what-is-github-codespaces-preview"></a>Co to jest GitHub Codespaces? (Wersja zapoznawcza)

Witamy w Codespaces! Cieszymy się, że jesteś tutaj.

Usługa GitHub Codespaces udostępnia środowisko programistyczne oparte na chmurze dla dowolnego działania, bez względu na to, czy jest to długoterminowy projekt, czy też krótkoterminowe zadanie, takie jak przeglądanie żądania ściągnięcia. Możesz korzystać z codespace z poziomu wersji zapoznawczej programu Visual Studio 2019 ([Utwórz konto w celu uzyskania ograniczonej publicznej wersji beta](https://github.com/features/codespaces/signup)).

Ponadto serwis GitHub Codespaces ma wiele zalet DevOps, takich jak powtarzalność i niezawodność, &mdash; które zwykle zostały zarezerwowane dla obciążeń produkcyjnych w &mdash; środowisku programistycznym. Możesz również personalizować usługę GitHub Codespaces, tak aby narzędzia, procesy i konfiguracje, których wolisz i z których korzystasz.

W tym dokumencie wyjaśniono kluczowe pojęcia i wprowadzono funkcje Codespaces. Jeśli chcesz zacząć, wypróbuj [Korzystanie z programu Visual Studio z codespace](use-visual-studio-with-codespaces.md).

> [!IMPORTANT]
> Aby korzystać z usługi GitHub Codespaces, należy zarejestrować się w celu uzyskania ograniczonej [publicznej wersji beta](https://github.com/features/codespaces/signup) . W okresie beta usługa GitHub nie zapewnia żadnych gwarancji dotyczących dostępności Codespaces. Aby uzyskać więcej informacji na temat dołączania do wersji beta, zobacz [Informacje o Codespaces](https://docs.github.com/github/developing-online-with-codespaces/about-codespaces#joining-the-beta).

## <a name="concepts-and-features"></a>Pojęcia i funkcje

Funkcje usługi GitHub Codespaces są tworzone w oparciu o kilka podstawowych pojęć. W tej sekcji omówiono te koncepcje i przedstawiono krótkie Przewodnik po funkcjach.

### <a name="remote-development"></a>Programowanie zdalne

Wielu deweloperów chce dzisiaj próbować kod w konfiguracjach zdalnych lub maszynach wirtualnych skonfigurowanych przy użyciu określonych stosów programowania i środowiska uruchomieniowego. Są tak, ponieważ są zbyt trudne, zbyt uciążliwe i w niektórych przypadkach, w najbliższym możliwym miejscu do konfigurowania tych środowisk programistycznych. Ponadto poszczególne osoby chcą wypróbować nowe technologie lub nowe struktury bez obaw o "obsłużenia" maszyn, których potrzebują do codziennej pracy.

Podczas korzystania ze środowisk zdalnych i narzędzi zdalnych umożliwiających deweloperom często naliczane są koszty związane z zarządzaniem maszyną. Konfiguracja środowiska często komplikuje dołączanie i przełączanie kontekstowe. W witrynie GitHub Codespaces są usuwane bariery do szybkiego dołączania i przełączania kontekstu przez włączenie wielu środowisk jednocześnie. 

W witrynie GitHub Codespaces dostępne są rozwiązania zarządzane umożliwiające skoncentrowanie się na produktywności przez Instalatora. W witrynie GitHub Codespaces koncepcyjnie i technicznie rozszerzono program Visual Studio 2019 do tworzenia zdalnego. 

### <a name="about-codespaces"></a>Informacje o codespaces

Codespace to połowa "zaplecza" w serwisie GitHub Codespaces. Jest to miejsce, w którym wykonywane są wszystkie obliczenia związane z tworzeniem oprogramowania: kompilowanie, debugowanie, przywracanie itp. Tworzenie codespace przygotowuje wszystko, czego potrzebujesz, aby zakończyć zadanie, przejrzeć żądanie ściągnięcia lub rozpocząć nowy projekt. Codespaces konfiguruje środowisko uruchomieniowe, kompilator, debuger, Edytor, niestandardowe konfiguracje dotfile i kod źródłowy wymagany do pracy nad projektem.

Usługa codespaces hostowana w chmurze zapewnia następujące korzyści:

- Są one szybkie i możliwe do utworzenia. Utwórz tyle rzeczy, ile potrzebujesz (limity kont), a następnie usuń je po zakończeniu.
- Są one zarządzane, co zmniejsza ogólną konserwację.
- Mają przewidywalne ceny i płacisz tylko za to, czego używasz. Ponadto wbudowano autowstrzymywanie w celu wyeliminowania pozostałych kosztów.
- Oszczędzają zasoby obliczeniowe. Przeniesienie obciążenia programowania do chmury powoduje zwolnienie ograniczonych zasobów na komputerze osobistym.

## <a name="custom-configuration"></a>Konfiguracja niestandardowa

Codespaces GitHub jest zbudowany w celu uwzględnienia szerokiej gamy projektów lub zadań. Można zacząć od funkcji konfiguracji inteligentnej, które udostępniają typowe ustawienia domyślne, lub dostrajać codespace z [konfiguracją niestandardową](customize-codespaces.md).

Elastyczna konfiguracja pozwala deweloperom na szybkie dołączanie do projektów z unikatowymi konfiguracjami i wymaganiami, które trudno stosować na komputerze lokalnym. Ponadto, odtwarzalny codespaces eliminuje problemy "działa na komputerze".

## <a name="personal-configuration"></a>Konfiguracja osobista

Wiemy, że zachowanie preferencji osobistych ma decydujące znaczenie dla rozwoju usługi w chmurze hostowanej przez chmurę codespace. W witrynie GitHub Codespacese indywidualne dostosowania na podstawie konfiguracji codespace. Osobiste preferencje i konfiguracje dla edytorów i terminali są obsługiwane przez Codespaces GitHub.

Codespace można utworzyć przy użyciu kolekcji [niestandardowych dotfiles](https://docs.github.com/github/developing-online-with-codespaces/personalizing-codespaces-for-your-account) (na przykład `.bashrc` `.gitconfig` itp.), a w usłudze GitHub Codespaces automatycznie jest synchronizowana tożsamość, motywy i ustawienia usługi git, dzięki czemu każdy codespace zostanie utworzony i będzie działać w taki sam sposób, niezależnie od możliwości środowiska specyficznego dla projektu.

## <a name="see-also"></a>Zobacz także

* [Jak używać programu Visual Studio z codespace](use-visual-studio-with-codespaces.md)
* [Jak dostosować codespace](customize-codespaces.md)
* [Obsługiwane funkcje programu Visual Studio](supported-features-codespaces.md)
