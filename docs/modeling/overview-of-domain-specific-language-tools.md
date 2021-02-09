---
title: Przegląd narzędzi językowych właściwych dla domeny
description: Dowiedz się, jak narzędzia DSL umożliwiają projektowanie języka specyficznego dla domeny, a następnie generowanie wszystkich elementów, które muszą być wymagane przez użytkowników w celu tworzenia modeli opartych na języku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dbae3a1b36e6a948766c7dc31d4a8ea8af6d70c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897765"
---
# <a name="overview-of-domain-specific-language-tools"></a>Przegląd narzędzi językowych właściwych dla domeny
Domain-Specific narzędzia języka (narzędzia DSL), które są hostowane w programie Visual Studio, umożliwiają projektowanie języka specyficznego dla domeny, a następnie generowanie wszystkich elementów, które użytkownicy muszą utworzyć, aby tworzyć modele oparte na języku.

 Narzędzia DSL zawierają następujące narzędzia:

- Kreator projektu korzystający z różnych szablonów rozwiązań ułatwiających rozpoczęcie tworzenia języka specyficznego dla domeny.

- Graficzny projektant służący do tworzenia i edytowania definicji języka specyficznego dla domeny.

- Aparat sprawdzania poprawności, który sprawdza, czy definicja języka specyficznego dla domeny jest poprawnie sformułowana, i wyświetla błędy i ostrzeżenia, jeśli występują problemy.

- Generator kodu, który pobiera definicję języka specyficznego dla domeny jako dane wejściowe i tworzy kod źródłowy jako dane wyjściowe.

## <a name="the-dsl-tools-solution"></a>Rozwiązanie narzędzi DSL
 Kreator Domain-Specific Designer udostępnia następujące szablony rozwiązań:

- Przepływ zadań

- Diagramy klas

- Minimalny język

- Modele składników

- Minimalna WPF

- Minimalne okna. Forms

- Biblioteka DSL

  Aby uzyskać więcej informacji, zobacz [Wybieranie szablonu rozwiązania Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Kreator tworzy rozwiązanie programu Visual Studio, które ma następujące projekty:

- DSL

   Projekt DSL definiuje język specyficzny dla domeny i narzędzia do edycji i przetwarzania.

- **DslPackage**

   Projekt DslPackage określa, jak narzędzia języka integrują się z programem Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>Interfejs graficzny narzędzi DSL
 Interfejs graficzny narzędzi DSL umożliwia dodawanie elementów i relacji do języka specyficznego dla domeny. Po dodaniu elementów można zdefiniować ich wygląd, mapując je do kształtów, dostosowując kolory i dodając dekoratory. Możesz również dodać elementy do przybornika.

## <a name="validation-in-dsl-tools"></a>Walidacja w narzędziach DSL
 Język DSL zapewnia jeden poziom walidacji, aby upewnić się, że model domeny spełnia podstawowe wymagania dotyczące generowania kodu. Zazwyczaj podczas tworzenia własnego języka specyficznego dla domeny należy dodać własne sprawdzanie poprawności, aby przedstawić reguły logiki biznesowej. Aby uzyskać więcej informacji na temat weryfikacji niestandardowej, zobacz [Walidacja w języku Domain-Specific](../modeling/validation-in-a-domain-specific-language.md).

 Zalecamy, aby sprawdzać, czy język specyficzny dla domeny jest często używany podczas projektowania. Jeśli w języku specyficznym dla domeny występują błędy walidacji, nie można wygenerować kodu źródłowego. Proces generowania kodu źródłowego z szablonów jest wykonywany przez kliknięcie przycisku **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań. Za każdym razem, gdy modyfikujesz definicję języka, pamiętaj również o **przekształceniu wszystkich szablonów**. Aby uzyskać więcej informacji, zobacz [How to: Create a Domain-Specific Language Solution](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Dostosowanie narzędzi DSL
 Możesz podać dodatkowy kod, aby uściślić zachowanie modelu i definiować ograniczenia w Twoim języku. W razie potrzeby można wprowadzić znaczące zmiany, modyfikując szablony tekstowe.

## <a name="distributing-your-dsl-solution"></a>Dystrybuowanie rozwiązania DSL
 Narzędzia DSL generują pakiet, który jest hostowany w programie Visual Studio. Pakiet wyświetla Przybornik, Eksplorator DSL i inne elementy interfejsu użytkownika, które umożliwiają użytkownikom tworzenie modeli przy użyciu języka specyficznego dla domeny.

 Podczas kompilowania i uruchamiania rozwiązania narzędzi DSL w programie Visual Studio drugie wystąpienie programu Visual Studio pokazuje, w jaki sposób język specyficzny dla domeny będzie wyglądał użytkownikowi w języku. Po zweryfikowaniu, że wszystko działa prawidłowo, można rozpowszechnić `.vsix` plik, który można znaleźć w folderze Build projektu DslPackage. Ten plik może służyć do instalowania programu DSL jako rozszerzenia programu Visual Studio na innych komputerach.  Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań językowych Domain-Specific](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Zobacz też

- [Wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md)
- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))