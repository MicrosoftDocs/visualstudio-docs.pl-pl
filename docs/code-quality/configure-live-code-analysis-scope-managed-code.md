---
title: Konfigurowanie zakresu analizy kodu na żywo dla kodu zarządzanego
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 300e3f276a45cfe2115311c7d27eedce365616cf
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432239"
---
# <a name="how-to-configure-live-code-analysis-scope-for-managed-code"></a>Jak: Konfigurowanie zakresu analizy kodu na żywo dla kodu zarządzanego

## <a name="what-is-live-code-analysis-for-managed-code"></a>Co to jest "Analiza kodu na żywo" dla kodu zarządzanego?
Visual Studio wykonuje kilka analiz kodu na żywo, również określane jako *analizy tła*, podczas edytowania plików źródłowych w edytorze. Niektóre z nich jest wymagana minimalna analiza dla akceptowalnego środowiska edycji IDE programu Visual Studio. Niektóre z nich jest dla poprawy responsywności dla funkcji IDE. Podczas gdy niektóre z nich jest, aby włączyć dodatkowe funkcje IDE, takie jak diagnostyka i poprawki kodu z analizatorów Roslyn. Na podstawie funkcji analizy te można pogrupować w następujący sposób:

- **Obliczenia w tle diagnostyki**: Analiza obliczania błędów, ostrzeżeń i sugestii w plikach źródłowych. Te diagnostyki są wyświetlane jako wpisy na liście błędów i jako squiggles w edytorze. Można je podzielić na dwie kategorie:
    - Diagnostyka kompilatora języka C# i Visual Basic
    - Diagnostyka analizatora Roslyn, która obejmuje:

        - Wbudowane analizatory IDE dla sugestii stylu kodu i
        - Pakiety analizatora innych firm [zainstalowane](./install-roslyn-analyzers.md) dla projektów w bieżącym rozwiązaniu.

- **Inne analizy w tle:** Analiza w celu poprawy reakcji i interakcji programu Visual Studio dla funkcji IDE. Oto kilka przykładów takich analiz:
    - Analizowanie w tle otwartych plików.
    - Kompilacja w tle projektów z otwartymi plikami w celu realizacji symboli dla lepszej responsywności niektórych funkcji IDE.
    - Tworzenie składni i symboli pamięci podręcznych.
    - Wykrywanie skojarzenia projektanta dla plików źródłowych, takich jak formularze, formanty itp.

## <a name="default-analysis-scope"></a>Domyślny zakres analizy

Domyślnie analiza kodu na żywo dla obliczeń w tle diagnostyki wykonuje dla wszystkich plików, które są _otwierane_ w programie Visual Studio. Niewiele _innych analiz w tle_ wymienionych powyżej wykonuje się dla wszystkich projektów, które mają co najmniej jeden otwarty plik. Podczas gdy kilka analiz tła wykonać dla całego rozwiązania.

## <a name="custom-analysis-scope"></a>Zakres analizy niestandardowej

Domyślny zakres każdej analizy tła został dostrojony pod kątem optymalnego środowiska użytkownika, funkcjonalności i wydajności dla większości scenariuszy i rozwiązań dla klientów. Istnieją jednak przypadki, w których klienci mogą chcieć dostosować ten zakres, aby zmniejszyć lub zwiększyć analizę tła. Przykład:

- Tryb oszczędzania energii: Jeśli użytkownicy pracują na baterii laptopa, mogą chcieć zminimalizować zużycie energii, aby wydłużyć czas pracy baterii. W tym scenariuszu chcieliby zminimalizować analizy w tle.
- Analiza kodu na żądanie: Jeśli użytkownicy wolą wyłączyć wykonywanie analizatora na żywo i ręcznie uruchomić analizę kodu na żądanie, chcieliby zminimalizować analizę w tle. Zobacz [Jak: Ręcznie uruchamiaj analizę kodu na żądanie](./how-to-run-code-analysis-manually-for-managed-code.md).
- Pełna analiza rozwiązania: Jeśli użytkownicy chcą zawsze zobaczyć wszystkie diagnostyki we wszystkich plikach w rozwiązaniu, niezależnie od tego, czy są one otwarte w edytorze, czy nie. W tym scenariuszu chcieliby zmaksymalizować zakres analizy w tle do całego rozwiązania.

Począwszy od programu Visual Studio 2019 w wersji 16.5, użytkownicy mogą jawnie dostosować zakres wszystkich analizy kodu na żywo, w tym obliczeń diagnostycznych dla projektów Języka C# i Visual Basic. Dostępne zakresy analizy to:

- **Bieżący dokument**: Minimalizuje zakres analizy kodu na żywo, aby wykonać tylko dla bieżącego lub widocznego pliku w edytorze.
- **Otwarte dokumenty**: Domyślny zakres analizy kodu na żywo, zgodnie z opisem w powyższej sekcji.
- **Całe rozwiązanie:** Maksymalizuje zakres analizy kodu na żywo do wykonania dla wszystkich plików i projektów w całym rozwiązaniu.

Możesz wybrać jeden z powyższych zakresów analizy niestandardowej w oknie dialogowym Opcje narzędzi, wykonując poniższe kroki:

1. Aby otworzyć okno dialogowe **Opcje,** na pasku menu w programie Visual Studio wybierz pozycję**Opcje** **narzędzi** > .

2. W oknie dialogowym **Opcje** wybierz pozycję **Edytor** > tekstu**C#** lub **Basic** > **Advanced**.

3. Wybierz żądany **zakres analizy w tle,** aby dostosować zakres analizy. Po zakończeniu wybierz przycisk **OK.**

![Zakres analizy.](./media/background-analysis-scope.png)

> [!NOTE]
> Przed programem Visual Studio 2019 w wersji 16.5 użytkownicy mogą dostosować zakres analizy obliczeń diagnostycznych do całego rozwiązania, korzystając z pola wyboru **Włącz pełną analizę rozwiązania** z karty **Tools** > **Options** > Text**Editor** > **C#** lub **Basic** > **Advanced.** Nie ma obsługi, aby zminimalizować zakres analizy w tle w poprzednich wersjach programu Visual Studio.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Automatyczne minimalizowanie zakresu analizy kodu na żywo

Jeśli program Visual Studio wykryje, że 200 MB lub mniej pamięci systemowej jest dostępna, automatycznie minimalizuje zakres analizy kodu na żywo do "Bieżący dokument". W takim przypadku pojawi się alert informujący, że program Visual Studio wyłączył niektóre funkcje. Przycisk umożliwia powrót do zakresu analizy wcześniejszej, jeśli chcesz.

![Tekst alertu minimalizujący zakres analizy](./media/fsa_alert.png)

## <a name="see-also"></a>Zobacz też

- [Automatyczne wstrzymanie funkcji](./automatic-feature-suspension.md)
- [Żądanie funkcji trybu oszczędzania energii](https://github.com/dotnet/roslyn/issues/38429)
