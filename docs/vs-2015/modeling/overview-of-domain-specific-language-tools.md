---
title: Przegląd narzędzia języka specyficznego dla domeny | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d38aed17d7fdaa694c8c5753705b28b0390dedfc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652143"
---
# <a name="overview-of-domain-specific-language-tools"></a>Przegląd narzędzi językowych właściwych dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzia języka specyficznego dla domeny (narzędzia DSL), które są hostowane w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , umożliwiają zaprojektowanie języka specyficznego dla domeny, a następnie wygenerowanie wszystkich elementów, które muszą być potrzebne użytkownikom do tworzenia modeli opartych na języku.

 Narzędzia DSL zawierają następujące narzędzia:

- Kreator projektu korzystający z różnych szablonów rozwiązań ułatwiających rozpoczęcie tworzenia języka specyficznego dla domeny.

- Graficzny projektant służący do tworzenia i edytowania definicji języka specyficznego dla domeny.

- Aparat sprawdzania poprawności, który sprawdza, czy definicja języka specyficznego dla domeny jest poprawnie sformułowana, i wyświetla błędy i ostrzeżenia, jeśli występują problemy.

- Generator kodu, który pobiera definicję języka specyficznego dla domeny jako dane wejściowe i tworzy kod źródłowy jako dane wyjściowe.

## <a name="the-dsl-tools-solution"></a>Rozwiązanie narzędzi DSL
 W Kreatorze projektanta specyficznego dla domeny dostępne są następujące szablony rozwiązań:

- Przepływ zadań

- Diagramy klas

- Minimalny język

- Modele składników

- Minimalna WPF

- Minimalne okna. Forms

- Biblioteka DSL

  Aby uzyskać więcej informacji, zobacz [Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Kreator tworzy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązanie, które ma następujące projekty:

- DSL

   Projekt DSL definiuje język specyficzny dla domeny i narzędzia do edycji i przetwarzania.

- **DslPackage**

   Projekt DslPackage określa, jak narzędzia języka integrują się z programem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="the-dsl-tools-graphical-interface"></a>Interfejs graficzny narzędzi DSL
 Interfejs graficzny narzędzi DSL umożliwia dodawanie elementów i relacji do języka specyficznego dla domeny. Po dodaniu elementów można zdefiniować ich wygląd, mapując je do kształtów, dostosowując kolory i dodając dekoratory. Możesz również dodać elementy do przybornika.

## <a name="validation-in-dsl-tools"></a>Walidacja w narzędziach DSL
 Język DSL zapewnia jeden poziom walidacji, aby upewnić się, że model domeny spełnia podstawowe wymagania dotyczące generowania kodu. Zazwyczaj podczas tworzenia własnego języka specyficznego dla domeny należy dodać własne sprawdzanie poprawności, aby przedstawić reguły logiki biznesowej. Aby uzyskać więcej informacji na temat weryfikacji niestandardowej, zobacz [Walidacja w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md).

 Zalecamy, aby sprawdzać, czy język specyficzny dla domeny jest często używany podczas projektowania. Jeśli w języku specyficznym dla domeny występują błędy walidacji, nie można wygenerować kodu źródłowego. Proces generowania kodu źródłowego z szablonów jest wykonywany przez kliknięcie przycisku **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań. Za każdym razem, gdy modyfikujesz definicję języka, pamiętaj również o **przekształceniu wszystkich szablonów**. Aby uzyskać więcej informacji, zobacz [How to: Create a specyficzne dla domeny rozwiązanie językowe](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Dostosowanie narzędzi DSL
 Możesz podać dodatkowy kod, aby uściślić zachowanie modelu i definiować ograniczenia w Twoim języku. W razie potrzeby można wprowadzić znaczące zmiany, modyfikując szablony tekstowe.

## <a name="distributing-your-dsl-solution"></a>Dystrybuowanie rozwiązania DSL
 Narzędzia DSL generują pakiet, który jest hostowany w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Pakiet wyświetla Przybornik, Eksplorator DSL i inne elementy interfejsu użytkownika, które umożliwiają użytkownikom tworzenie modeli przy użyciu języka specyficznego dla domeny.

 Podczas kompilowania i uruchamiania rozwiązania narzędzi DSL w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] drugie wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pokazuje, w jaki sposób język specyficzny dla domeny będzie wyglądał użytkownikowi w języku. Po zweryfikowaniu, że wszystko działa prawidłowo, można rozpowszechnić `.vsix` plik, który można znaleźć w folderze Build projektu DslPackage. Ten plik może służyć do instalowania programu DSL jako [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia na innych komputerach.  Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań językowych właściwych dla domeny](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Zobacz też
 [Eksperymentalne wystąpienie](../extensibility/the-experimental-instance.md) [Narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
