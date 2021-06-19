---
title: Przegląd narzędzi językowych właściwych dla domeny
description: Dowiedz się, jak narzędzia DSL umożliwiają projektowanie języka specyficznego dla domeny, a następnie generowanie wszystkiego, co użytkownicy muszą mieć do tworzenia modeli opartych na języku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 004c9929b33878359fa23735189d60939953755a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390909"
---
# <a name="overview-of-domain-specific-language-tools"></a>Przegląd narzędzi językowych właściwych dla domeny
Domain-Specific Language Tools (DSL Tools), które są hostowane w języku Visual Studio, umożliwiają projektowanie języka specyficznego dla domeny, a następnie generowanie wszystkiego, co użytkownicy muszą tworzyć modele oparte na języku.

 W narzędziach DSL dostępne są następujące narzędzia:

- Kreator projektu, który używa różnych szablonów rozwiązań, aby ułatwić rozpoczęcie tworzenia języka specyficznego dla domeny.

- Projektant graficzny do tworzenia i edytowania definicji języka specyficznego dla domeny.

- Aparat weryfikacji, który zapewnia, że definicja języka specyficznego dla domeny jest dobrze formowana, oraz wyświetla błędy i ostrzeżenia w przypadku problemów.

- Generator kodu, który przyjmuje definicję języka specyficzną dla domeny jako dane wejściowe i generuje kod źródłowy jako dane wyjściowe.

## <a name="the-dsl-tools-solution"></a>Rozwiązanie dsl tools
 Kreator Domain-Specific projektanta aplikacji udostępnia następujące szablony rozwiązań:

- Przepływ zadań

- Diagramy klas

- Minimalny język

- Modele składników

- Minimalna WPF

- Minimalne formularze Windows.Forms

- Biblioteka DSL

  Aby uzyskać więcej informacji, zobacz Choosing a Domain-Specific Language Solution Template (Wybieranie szablonu [rozwiązania języka Domain-Specific językowego).](../modeling/choosing-a-domain-specific-language-solution-template.md)

  Kreator tworzy Visual Studio, które ma następujące projekty:

- Dsl

   Projekt Dsl definiuje język specyficzny dla domeny oraz jego narzędzia do edytowania i przetwarzania.

- **Dslpackage**

   Projekt DslPackage określa sposób integracji narzędzi językowych z Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>Interfejs graficzny narzędzi DSL
 Interfejs graficzny narzędzi DSL umożliwia dodawanie elementów i relacji do języka specyficznego dla domeny. Po dodaniu elementów można zdefiniować ich wygląd, mapując je na kształty, do dostosowywania kolorów i dodając dekoratory. Elementy można również dodać do przybornika.

## <a name="validation-in-dsl-tools"></a>Walidacja w narzędziach DSL
 Dsl zapewnia jeden poziom weryfikacji, aby upewnić się, że model domeny spełnia podstawowe wymagania dotyczące generowania kodu. Zazwyczaj podczas tworzenia własnego języka specyficznego dla domeny należy dodać własną walidację w celu wyrażenia reguł logiki biznesowej. Aby uzyskać więcej informacji na temat walidacji niestandardowej, zobacz Validation in a Domain-Specific Language (Walidacja [w Domain-Specific języku](../modeling/validation-in-a-domain-specific-language.md)).

 Zalecamy, aby podczas projektowania często sprawdzać poprawność języka specyficznego dla domeny. Jeśli w języku specyficznym dla domeny występują błędy weryfikacji, nie można wygenerować kodu źródłowego. Proces generowania kodu źródłowego z szablonów jest wykonywany przez kliknięcie pozycji Przekształć **wszystkie** szablony na pasku narzędzi Eksplorator rozwiązań. Zawsze, gdy modyfikujesz definicję języka, pamiętaj również, aby **przekształć wszystkie szablony.** Aby uzyskać więcej informacji, zobacz How to: Create a Domain-Specific Language Solution (Jak utworzyć rozwiązanie [Domain-Specific językowego).](../modeling/how-to-create-a-domain-specific-language-solution.md)

## <a name="customization-of-dsl-tools"></a>Dostosowywanie narzędzi DSL
 Możesz podać dodatkowy kod, aby uściślić zachowanie modelu i zdefiniować ograniczenia dotyczące języka. W razie potrzeby można wprowadzić znaczące zmiany, modyfikując szablony tekstowe.

## <a name="distributing-your-dsl-solution"></a>Dystrybucja rozwiązania DSL
 Narzędzia DSL Generuje pakiet, który jest hostowany w Visual Studio. Pakiet wyświetla przybornik, eksplorator DSL i inne elementy interfejsu użytkownika, które umożliwiają użytkownikom tworzenie modeli przy użyciu języka specyficznego dla domeny.

 Podczas kompilowania i uruchamiania rozwiązania DSL Tools w języku Visual Studio drugie wystąpienie usługi Visual Studio pokazuje, jak język specyficzny dla domeny wygląda dla użytkownika języka. Po sprawdzeniu, czy wszystko działa prawidłowo, możesz rozpowszechnić plik, który znajdziesz w `.vsix` folderze kompilacji projektu DslPackage. Ten plik może służyć do instalowania DSL jako rozszerzenie Visual Studio na innych komputerach.  Aby uzyskać więcej informacji, zobacz [Wdrażanie Domain-Specific Language Solutions.](msi-and-vsix-deployment-of-a-dsl.md)

## <a name="see-also"></a>Zobacz też

- [Wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md)
- [narzędzia języka specyficznego dla domeny słownika](/previous-versions/bb126564(v=vs.100))