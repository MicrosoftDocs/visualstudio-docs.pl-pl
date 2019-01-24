---
title: Program Visual Studio Isolated Shell | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59ecd079b7e95d86ab85eb9e5e36fcf938f99f58
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54784860"
---
# <a name="visual-studio-isolated-shell"></a>Program Visual Studio Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Powłoka programu Visual Studio, izolowany umożliwia tworzenie autonomicznych aplikacji, które można uruchomić side-by-side z innymi wersjami programu Visual Studio. Jest używany przede wszystkim do hostowania specjalistycznych narzędzi, które mogą używać usług Visual Studio, ale również mieć z dostosowanego wyglądu znakowania. Funkcje programu Visual Studio i grupami polecenia menu mogą być łatwo włączać i wyłączać. Tytuły aplikacji, ikony aplikacji i ekrany powitalne są w pełni konfigurowalne. Aby uzyskać listę funkcji można dostosowywać, zobacz [Dostosowywanie programu Isolated Shell](../extensibility/customizing-the-isolated-shell.md).  
  
 Aby pracować z projektu programu shell w trybie izolowanym, należy zainstalować zestawu SDK programu Visual Studio. Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Do tworzenia aplikacji isolated shell, Rozpocznij od projektu programu Visual Studio Shell izolowanym. Ten projekt zawiera wszystko, czego potrzebujesz do tworzenia i testowania aplikacji izolowanej powłoki. Gdy jesteś gotowy do zapisu w programu instalacyjnego, która wdraża aplikację, należy pobrać pakiet redystrybucyjny programu shell w trybie izolowanym z [pakiet redystrybucyjny Microsoft Visual Studio Shell (Isolated)](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Aby korzystać z pakietu redystrybucyjnego programu shell w trybie izolowanym, poprosimy Cię o ankiety klientów.  Po wypełnieniu ankiety, nastąpi przekierowanie do strony Visual Studio Connect zawierającej łącza pobierania pakietów redystrybucyjnych.  Łącza pobierania podczas kolejnych wizyt w witrynie Visual Studio Connect, w obszarze **programy &#124; VISUAL STUDIO 2015 ZINTEGROWANE i ISOLATED SHELL** kartę.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji o sposobie wdrażania aplikacji opartych na powłoce izolowanej zobacz [instruktażu: Tworzenie prostej Isolated Shell aplikacji](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Praca z programu isolated shell  
 Aplikacji powłoki programu Visual Studio, izolowany ma pełny dostęp do usług Visual Studio i obsługuje specjalnego dostosowania, znakowania. Istnieje kilka sposobów, które można dostosować aplikacji isolated shell:  
  
- Składniki pakietów VSPackage a Managed Extensibility Framework (MEF) umożliwia rozszerzanie aplikacji isolated shell, tak samo, jak mogłaby być używana w inne rozszerzenia programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Rozszerzanie programu Isolated Shell](../extensibility/extending-the-isolated-shell.md).  
  
- Aby funkcje programu Visual Studio i grup poleceń menu dostępne lub niedostępne, należy zaktualizować pliku vsct w projekcie interfejsu użytkownika aplikacji.  
  
- Aby usunąć **opcje** stron lub innych składników powłoki programu Visual Studio z poziomu aplikacji, należy zaktualizować pliku pkgundef aplikacji.  
  
- Aby zmodyfikować inne aspekty wygląd lub zachowanie powłoki, należy zaktualizować plik .pkgdef aplikacji.  
  
- Niektóre aspekty powłoki można również określić po uruchomieniu aplikacji. Aby to zrobić, zaktualizuj parametry w wywołaniu punkt wejścia Start appenvstub.dll.  
  
  Aby uzyskać więcej informacji na temat różnych elementów, które można dostosować, zobacz [elementy programu Isolated Shell](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Standardowe funkcje programu Isolated Shell  
 Następujące funkcje są standardowe dla wszystkich edycji programu Visual Studio.  
  
|Kategoria funkcji|Funkcja|  
|----------------------|-------------|  
|Funkcje środowiska IDE|Ustawienia importu/eksportu<br /><br /> Instalator kontrolki przybornika<br /><br /> Lista zadań & Lista błędów<br /><br /> Okno wyniku<br /><br /> Strona początkowa<br /><br /> Okno Właściwości<br /><br /> Przybornik<br /><br /> Eksplorator rozwiązań<br /><br /> Okno zakładek<br /><br /> Widok klas<br /><br /> Przeglądarka obiektów<br /><br /> Okno polecenia<br /><br /> Konspekt dokumentu<br /><br /> Widok zasobów<br /><br /> Narzędzie zewnętrzne<br /><br /> Windows Communication Foundation (WCF) Dodaj odwołanie do usługi<br /><br /> Language Integrated Query (LINQ) pomocy technicznej|  
|Projektant/Edytor|Kod przeglądający narzędzia (ujednolicone wyszukiwanie, definicja źródła, dziedziczenie)<br /><br /> IntelliSense<br /><br /> SmartTags<br /><br /> Menedżer fragmentów kodu<br /><br /> Wstawki kodu<br /><br /> Refaktoryzacja<br /><br /> Lista pretty<br /><br /> Filtrowanie IntelliSense<br /><br /> Okno definicji kodu<br /><br /> Projektant aplikacji<br /><br /> Projektant Windows Forms<br /><br /> Projektant programu Windows Presentation Foundation (WPF)|  
|Debugowanie|Ewaluator wyrażeń C#<br /><br /> Debugowanie lokalne<br /><br /> Zarządzanie debugowaniem<br /><br /> Edytuj i kontynuuj<br /><br /> Debugowanie między wątkami<br /><br /> wizualizacje<br /><br /> DataTips<br /><br /> Debugowanie w trybie macierzystym<br /><br /> Debugowanie skryptów<br /><br /> Debugowania międzyoperacyjnego<br /><br /> Debugowanie just-in-time (JIT)<br /><br /> Debugowanie wielu procesów<br /><br /> Debugowanie kodu XSLT<br /><br /> Dołącz do procesu lokalnego<br /><br /> Punkty śledzenia<br /><br /> Ograniczenia punktu przerwania|  
|Dane|Eksplorator serwera (uproszczony — tylko dane)<br /><br /> Powiązanie danych z danymi lokalnymi (. MDF lub. MDB)<br /><br /> Powiązanie danych z obiektu<br /><br /> Powiązanie danych z usługi sieci Web<br /><br /> Pełny zestaw formantów danych<br /><br /> Edytor XML<br /><br /> Powiąż dane z lokalnej bazy danych serwera<br /><br /> Data Sources — Okno|  
|sieć Web|Edytor HTML<br /><br /> Przeglądarki sieci Web<br /><br /> Projektant formularzy sieci Web<br /><br /> Projekt witryny sieci Web<br /><br /> Projekt aplikacji sieci Web|  
|Rozszerzalność|Wykorzystuje składniki pakietów VSPackage i MEF|  
  
## <a name="see-also"></a>Zobacz też  
 [Shell (Isolated lub Integrated)](../extensibility/shell-isolated-or-integrated.md)
