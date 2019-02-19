---
title: Wprowadzenie do aplikacji międzynarodowych oparte na programie .NET Framework | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- strings [Visual Studio], localizing
- Web applications [.NET Framework], globalization
- Windows Forms, globalization
- localization [Visual Studio], culture setting
- fallback resources
- culture, setting
- globalization [Visual Studio], culture setting
- resources [Visual Studio], localization
- localization [Visual Studio], .NET localization model
- Assembly Resource file template
- resources [Visual Studio], fallback system
- international applications [Visual Studio], about international applications
- globalization [Visual Studio], international applications
- ASP.NET, globalization
- resource files, fallback processes
- user interface, culture setting
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86ca63ead6b2014dfe0d90d496ef4b7d7efe7f63
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54784803"
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>Wprowadzenie do aplikacji międzynarodowych na podstawie .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], istnieją dwie części do tworzenia aplikacji gotowych do: globalizacja, proces projektowania aplikacji, które dostosowują się do różnych kultur i lokalizacja, proces tłumaczeniem zasobów dla określonej kultury. Aby uzyskać ogólne informacje dotyczące projektowania aplikacji międzynarodowych odbiorców, zobacz [najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych](http://msdn.microsoft.com/library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c).  
  
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Model lokalizacji składa się z głównym zestawie, który zawiera kod aplikacji i zasoby rezerwowe — ciągi, obrazy i inne obiekty, dla języka, w którym pierwotnie opracowano aplikację. Każda aplikacja zlokalizowanych ma zestawy satelickie lub zespołów, które zawierają zlokalizowane zasoby. Ponieważ zawsze zestawu głównego zawiera zasoby rezerwowe, jeśli zasób nie zostanie znaleziony w zestawie satelickim zlokalizowane, <xref:System.Resources.ResourceManager> spróbuje ją załadować hierarchicznie ostatecznie nastąpi powrót do zasobu w głównym zestawie. System rezerwowy zasobu zostało wyjaśnione bardziej szczegółowo w [hierarchiczna organizacja zasobów do lokalizacji](../ide/hierarchical-organization-of-resources-for-localization.md).  
  
 Jeden zasób lokalizacji, należy rozważyć użycie jest słownik do firmy Microsoft zlokalizowany produktów. Ten plik CSV zawiera ponad 12 000 terminy w języku angielskim oraz tłumaczenia warunki maksymalnie 59 różnych językach. Słownik jest dostępny do pobrania [tłumaczenia terminologii firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=128146) strony sieci Web.  
  
 System projektu dla aplikacji Windows Forms można wygenerować plików zasobów dla obu plan awaryjny i każdego żądanego dodatkowe kultury interfejsu użytkownika. Plik zasobów rezerwowego jest wbudowana w głównym zestawie, a pliki zasobów dla kultury następnie są tworzone w zestawy satelit, jeden dla każdej kultury interfejsu użytkownika. Podczas tworzenia projektu, pliki zasobów są kompilowane z formatu programu Visual Studio XML (resx) na pośrednie format binarny (.resources), które następnie są osadzone w zestawach satelickich.  
  
 System projektu dla Windows Forms i formularzy sieci Web pozwala na tworzenie plików zasobów przy użyciu szablonu usługi plik zasobów zestawu, dostęp do zasobów i skompiluj projekt. Zestawy satelickie zostanie utworzony wraz z zestawu głównego.  
  
 Po wykonaniu zlokalizowanych aplikacji, jego wygląd jest określany przez dwie wartości kultury. (A *kultury* jest zestawem preferencje użytkownika dotyczące języka, środowiska i Konwencji kultury użytkownika.) Ustawienie kultury interfejsu użytkownika określa, jakie zasoby zostaną załadowane. Kultura interfejsu użytkownika jest ustawiony jako `UICulture` w plikach Web.config i dyrektyw strony i <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> w kodzie języka Visual Basic lub Visual C#. Ustawienia kulturowe Określa formatowanie wartości, takich jak daty, liczby, waluty i tak dalej. Kultura jest ustawiony jako `Culture` w plikach Web.config i dyrektywy strony <xref:System.Globalization.CultureInfo.CurrentCulture%2A> w kodzie języka Visual Basic lub Visual C#.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Globalization>   
 <xref:System.Resources>   
 [Globalizacja i lokalizacja aplikacji](../ide/globalizing-and-localizing-applications.md)   
 [Zabezpieczenia a zlokalizowane zestawy satelickie](../ide/security-and-localized-satellite-assemblies.md)
