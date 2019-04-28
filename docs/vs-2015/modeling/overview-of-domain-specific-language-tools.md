---
title: Przegląd narzędzi języka specyficznego dla domeny | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d36b2cb0c4e8e7ddf9016302c9efcfae0710097c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62568359"
---
# <a name="overview-of-domain-specific-language-tools"></a>Przegląd narzędzi językowych właściwych dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzia języka specyficznego dla domeny (narzędzia DSL), które są hostowane na platformie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], pozwala projektować języka specyficznego dla domeny, a następnie wygenerować wszystko, co użytkownicy muszą mieć do tworzenia modeli, które są oparte na języku.  
  
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
  
  Kreator utworzy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązanie, które ma następujące projekty:  
  
- Dsl  
  
   Projektu Dsl definiuje języka specyficznego dla domeny i jego narzędzi edycji i przetwarzania.  
  
- **DslPackage**  
  
   Projekt DslPackage Określa, jak narzędzia językowe zintegrować z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="the-dsl-tools-graphical-interface"></a>Interfejsu graficznego narzędzia DSL  
 Aby dodać elementy i relacje do języka specyficznego dla domeny, można użyć interfejsu graficznego narzędzia DSL. Po dodaniu elementów można zdefiniować ich wygląd, mapując je do kształtów zewnętrznych, dostosowywanie kolorów i dodawanie dekoratory. Możesz również dodać elementy do przybornika.  
  
## <a name="validation-in-dsl-tools"></a>Sprawdzanie poprawności w narzędzia DSL  
 Język DSL zapewnia jeden poziom sprawdzania poprawności, aby upewnić się, że model domeny spełnia wymagania podstawowe do generowania kodu. Zwykle podczas tworzenia języka specyficznego dla domeny, możesz dodać weryfikację określenie reguł logiki biznesowej. Aby uzyskać więcej informacji na temat niestandardowego sprawdzania poprawności, zobacz [weryfikacji języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).  
  
 Zaleca się sprawdzenie poprawności języka specyficznego dla domeny często podczas projektowania. Jeśli języka specyficznego dla domeny ma błędy sprawdzania poprawności, nie można wygenerować kodu źródłowego. Proces generowania kodu źródłowego z szablonów odbywa się przez kliknięcie przycisku **Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań. Przy każdej modyfikacji definicji języka Pamiętaj również o **Przekształć wszystkie szablony**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie rozwiązania języka dotyczącego określonej domeny](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="customization-of-dsl-tools"></a>Dostosowywanie narzędzia DSL  
 Możesz podać dodatkowe kodu, aby dostosować zachowanie w modelu i zdefiniować ograniczenia za pośrednictwem języka. W razie potrzeby możesz wprowadzeniem znaczących zmian, modyfikując szablony tekstowe.  
  
## <a name="distributing-your-dsl-solution"></a>Dystrybucja rozwiązania DSL  
 Narzędzia DSL generuje pakiet, który jest hostowany w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pakiet Wyświetla przybornik, Eksplorator DSL i inne elementy interfejsu użytkownika, które pozwalają użytkownikom tworzyć modele przy użyciu języka specyficznego dla domeny.  
  
 Podczas kompilowania i uruchamiania rozwiązań narzędzia DSL [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], drugie wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dowiesz się, jak wygląda języka specyficznego dla domeny użytkownika języka. Po upewnieniu się, że wszystko działa poprawnie, można rozpowszechniać `.vsix` pliku, który znajduje się w folderze kompilacji testowanego projektu DslPackage. Ten plik może służyć do instalowania DSL jako [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia na innych komputerach.  Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązań języka dotyczącego określonej domeny](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md)   
 [Słownik narzędzi języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
