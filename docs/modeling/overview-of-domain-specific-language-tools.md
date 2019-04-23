---
title: Przegląd narzędzi językowych właściwych dla domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e31d9c01ded7754fd10419f3fd0e18d9616a51eb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078242"
---
# <a name="overview-of-domain-specific-language-tools"></a>Przegląd narzędzi językowych właściwych dla domeny
Narzędzia języka specyficznego dla domeny (narzędzia DSL), które są hostowane w programie Visual Studio, pozwalają na projektowanie języka specyficznego dla domeny, a następnie wygenerować wszystko, co użytkownicy muszą mieć do tworzenia modeli, które są oparte na języku.

 Narzędzia DSL obejmuje następujące narzędzia:

- Kreator projektu, który używa innego rozwiązania szablonów, które ułatwią rozpoczęcie tworzenia języka specyficznego dla domeny.

- Graficzny projektant do tworzenia i edytowania definicji języka specyficznego dla domeny.

- Aparat sprawdzania poprawności upewnia się, że definicji języka specyficznego dla domeny jest dobrze sformułowany i wyświetla błędy i ostrzeżenia, jeśli wystąpią problemy.

- Generator kodu, który przyjmuje definicji języka specyficznego dla domeny jako dane wejściowe i generuje kod źródłowy jako dane wyjściowe.

## <a name="the-dsl-tools-solution"></a>Rozwiązanie narzędzi języka DSL
 Kreator projektanta specyficznego dla domeny zawiera następujące szablony rozwiązań:

- Przepływ zadań

- Diagramy klas

- Minimalny języka

- Modele składnika

- Minimalny WPF

- Minimal Windows.Forms

- Biblioteka DSL

  Aby uzyskać więcej informacji, zobacz [Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Kreator utworzy rozwiązanie programu Visual Studio, które ma następujące projekty:

- Dsl

   Projektu Dsl definiuje języka specyficznego dla domeny i jego narzędzi edycji i przetwarzania.

- **DslPackage**

   Projekt DslPackage Określa, jak narzędzia językowe zintegrować z programem Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>Interfejsu graficznego narzędzia DSL
 Aby dodać elementy i relacje do języka specyficznego dla domeny, można użyć interfejsu graficznego narzędzia DSL. Po dodaniu elementów można zdefiniować ich wygląd, mapując je do kształtów zewnętrznych, dostosowywanie kolorów i dodawanie dekoratory. Możesz również dodać elementy do przybornika.

## <a name="validation-in-dsl-tools"></a>Sprawdzanie poprawności w narzędzia DSL
 Język DSL zapewnia jeden poziom sprawdzania poprawności, aby upewnić się, że model domeny spełnia wymagania podstawowe do generowania kodu. Zwykle podczas tworzenia języka specyficznego dla domeny, możesz dodać weryfikację określenie reguł logiki biznesowej. Aby uzyskać więcej informacji na temat niestandardowego sprawdzania poprawności, zobacz [weryfikacji języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).

 Zaleca się sprawdzenie poprawności języka specyficznego dla domeny często podczas projektowania. Jeśli języka specyficznego dla domeny ma błędy sprawdzania poprawności, nie można wygenerować kodu źródłowego. Proces generowania kodu źródłowego z szablonów odbywa się przez kliknięcie przycisku **Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań. Przy każdej modyfikacji definicji języka Pamiętaj również o **Przekształć wszystkie szablony**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie rozwiązania języka dotyczącego określonej domeny](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Dostosowywanie narzędzia DSL
 Możesz podać dodatkowe kodu, aby dostosować zachowanie w modelu i zdefiniować ograniczenia za pośrednictwem języka. W razie potrzeby możesz wprowadzeniem znaczących zmian, modyfikując szablony tekstowe.

## <a name="distributing-your-dsl-solution"></a>Dystrybucja rozwiązania DSL
 Narzędzia DSL generuje pakiet, który znajduje się w programie Visual Studio. Pakiet Wyświetla przybornik, Eksplorator DSL i inne elementy interfejsu użytkownika, które pozwalają użytkownikom tworzyć modele przy użyciu języka specyficznego dla domeny.

 Po skompilować i uruchomić rozwiązanie narzędzia DSL w programie Visual Studio, drugie wystąpienie programu Visual Studio pokazuje, jak wygląda języka specyficznego dla domeny użytkownika języka. Po upewnieniu się, że wszystko działa poprawnie, można rozpowszechniać `.vsix` pliku, który znajduje się w folderze kompilacji testowanego projektu DslPackage. Ten plik można zainstalować język DSL jako rozszerzenia programu Visual Studio na innych komputerach.  Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązań języka dotyczącego określonej domeny](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Zobacz też

- [Wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md)
- [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)