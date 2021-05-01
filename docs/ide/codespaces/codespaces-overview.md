---
title: Omówienie usługi GitHub Codespaces (wersja zapoznawcza)
description: Dowiedz się więcej o środowisku GitHub Codespaces Visual Studio o tym, jak może pomóc w rozszerzeniu środowiska projektowego na chmurę.
ms.topic: overview
ms.date: 09/04/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: ab50c3c2df2cfad6d489d800f47624503844dc9d
ms.sourcegitcommit: a667ce8394a800906d633737f4fcbc77f0fcba7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2021
ms.locfileid: "108298746"
---
# <a name="what-is-github-codespaces-preview"></a>Co to jest GitHub Codespaces? (Wersja zapoznawcza)

> [!Important]
> Od 12 kwietnia 2021 r. łączenie się z platformą GitHub Codespaces od Visual Studio 2019 r. nie będzie już obsługiwane i ta prywatna wersja zapoznawcza została zakończona. Koncentrujemy się na rozwijających się doświadczeniach w zakresie wewnętrznej pętli chmurowej i rozwiązań VDI zoptymalizowanych pod kątem szerokiego Visual Studio obciążeń. Zachęcamy do udziału w naszym [forum](https://developercommunity.visualstudio.com/home) społeczności deweloperów, na Visual Studio uzyskać informacje na temat przyszłych wersji zapoznawczych i informacji o planach.

Witamy w codespaces! Cieszymy się, że jesteś tutaj.

Usługa GitHub Codespaces zapewnia środowisko deweloperskie oparte na chmurze dla dowolnych działań, zarówno w przypadku projektów długoterminowych, jak i krótkoterminowych, takich jak przeglądanie żądania ściągnowania.

Ponadto usługa GitHub Codespaces oferuje wiele zalet metodyki DevOps, takich jak powtarzalność i niezawodność, które są zwykle zarezerwowane dla obciążeń produkcyjnych w środowisku &mdash; &mdash; deweloperskim. Możesz również spersonalizować usługę GitHub Codespaces, aby dostępne były również preferowane narzędzia, procesy i konfiguracje.

W tym dokumencie objaśnimy kluczowe pojęcia i przedstawimy funkcje codespaces. Jeśli chcesz rozpocząć pracę, zobacz Use Visual Studio with a codespace (Używanie Visual Studio [z przestrzenią kodu).](use-visual-studio-with-codespaces.md)

## <a name="concepts-and-features"></a>Pojęcia i funkcje

Funkcje usługi GitHub Codespaces są zbudowane na kilku podstawowych pojęciach. Ta sekcja obejmuje te pojęcia i zawiera krótki przewodnik po funkcjach.

### <a name="remote-development"></a>Opracowywanie zdalne

Obecnie wielu deweloperów próbuje kodować w konfiguracjach zdalnych lub na komputerach wirtualnych, które są skonfigurowane z określonymi stosami deweloperskich i uruchomieniowych. Robisz to, ponieważ jest to zbyt trudne, zbyt uciążliwe, a w niektórych przypadkach niemal niemożliwe do skonfigurowania tych środowisk deweloperskich lokalnie. Ponadto poszczególne osoby chcą wypróbować nowe technologie lub nowe struktury bez obaw o "załadanie" maszyn, których potrzebują do pracy.

Chociaż korzystanie ze zdalnych środowisk i narzędzi z możliwościami zdalnymi zwiększa możliwości deweloperów, często występuje obciążenie związane z zarządzaniem maszynami. Konfiguracja środowiska często komplikuje dołączanie i przełączanie kontekstu. Usługa GitHub Codespaces usuwa bariery dla szybkiego dołączania i przełączania kontekstu, umożliwiając jednoczesne istniejące wiele środowisk.

Usługa GitHub Codespaces udostępnia rozwiązania zarządzane, które pozwalają skupić się na produktywności nad konfiguracją. Usługa GitHub Codespaces koncepcyjnie i technicznie rozszerza Visual Studio 2019 r. na tworzenie aplikacji zdalnych.

### <a name="about-codespaces"></a>Informacje o przestrzeniach kodu

Obszar codespace jest "zaplecza" połową usługi GitHub Codespaces. Jest to miejsce, w którym odbywa się wszystkie obliczenia związane z tworzeniem oprogramowania: kompilowanie, debugowanie, przywracanie itp. Utworzenie przestrzeni kodu przygotowuje wszystko, czego potrzebujesz do ukończenia zadania, przejrzenia lub uruchomienia nowego projektu. Środowisko Codespaces konfiguruje środowisko uruchomieniowe, kompilator, debuger, edytor, niestandardowe konfiguracje pliku dotfile oraz kod źródłowy wymagany do pracy nad projektem.

Przestrzenie kodu hostowane w chmurze zapewniają następujące korzyści:

- Można je szybko tworzyć i tworzyć. Utwórz tyle, ile potrzebujesz (zgodnie z limitami konta), a następnie po zakończeniu je usuwaj.
- Są one zarządzane, co zmniejsza ogólną konserwację.
- Mają one przewidywalne ceny, a Ty płacisz tylko za to, czego używasz. Ponadto istnieje wbudowane automatyczne podsułanie w celu wyeliminowania runaway kosztów.
- Oszczędzają zasoby obliczeniowe. Przeniesienie obciążenia programowego do chmury pozwala uwolnić ograniczone zasoby na komputerze osobistym.

## <a name="custom-configuration"></a>Konfiguracja niestandardowa

Usługa GitHub Codespaces została zbudowana w celu uwzględnienia najszerszego rodzaju projektów lub zadań. Możesz rozpocząć od inteligentnych funkcji konfiguracji, które zapewniają typowe wartości domyślne, lub dostosować obszar kodu przy użyciu [konfiguracji niestandardowej.](customize-codespaces.md)

Elastyczna konfiguracja umożliwia deweloperom szybkie dołączanie do projektów o unikatowej konfiguracji i wymaganiach, które są trudne do zastosowania na komputerze lokalnym. Ponadto powtarzalne przestrzenie kodu eliminują problemy "działa na mojej maszynie".

## <a name="personal-configuration"></a>Konfiguracja osobista

Wiemy, że zachowywanie osobistych preferencji ma kluczowe znaczenie dla tego, aby programowanie w środowisku codespace hostowanych w chmurze było znane i naturalne. Usługa GitHub Codespaces warstwy indywidualizowanych dostosowań na podstawie konfiguracji usługi Codespaces. Osobiste preferencje i konfiguracja dla edytorów i terminali są obsługiwane przez usługę GitHub Codespaces.

Przestrzeń kodowa może zostać utworzona za pomocą kolekcji niestandardowych plików [dotfile](https://docs.github.com/github/developing-online-with-codespaces/personalizing-codespaces-for-your-account) specyficznych dla użytkownika (na przykład , itp.), a usługa `.bashrc` GitHub Codespaces automatycznie synchronizuje tożsamość, motywy i ustawienia usługi Git, tak aby każdy tworzony obszar kodu wyglądał i wyglądał zgodnie z potrzebami, niezależnie od możliwości środowiska specyficznego dla `.gitconfig` projektu.

## <a name="see-also"></a>Zobacz też

* [Jak używać Visual Studio z przestrzenią kodu](use-visual-studio-with-codespaces.md)
* [Jak dostosować przestrzeń kodów](customize-codespaces.md)
* [Obsługiwane funkcje programu Visual Studio](supported-features-codespaces.md)
