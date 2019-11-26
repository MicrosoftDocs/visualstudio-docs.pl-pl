---
title: Powłoka izolowana programu Visual Studio | Microsoft Docs
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
ms.openlocfilehash: 36491d9d590a45256e297654f71652ab5de5cd98
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299718"
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio Shell (izolowany)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Izolowana powłoka programu Visual Studio umożliwia tworzenie autonomicznych aplikacji, które mogą być uruchamiane równolegle z innymi wersjami programu Visual Studio. Jest ona używana głównie do hostowania wyspecjalizowanych narzędzi, które mogą korzystać z usług Visual Studio, ale również mieć dostosowany wygląd i markę. Funkcje programu Visual Studio i grupy poleceń menu można łatwo włączać i wyłączać. Tytuły aplikacji, ikony aplikacji i ekrany powitalne są w pełni dostosowywane. Listę dostosowywalnych funkcji można znaleźć w temacie [Dostosowywanie powłoki izolowanej](../extensibility/customizing-the-isolated-shell.md).  
  
 Aby można było korzystać z odizolowanego projektu powłoki, należy zainstalować Visual Studio SDK. Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Aby utworzyć izolowaną aplikację powłoki, Zacznij od projektu programu Visual Studio Shell izolowanego. Ten projekt zawiera wszystko, czego potrzebujesz do opracowania i przetestowania własnej aplikacji powłoki izolowanej. Gdy wszystko jest gotowe do napisania programu instalacyjnego, który wdraża aplikację, należy uzyskać pakiet redystrybucyjny izolowanej powłoki z [Microsoft Visual Studio Shell (izolowany) pakietu redystrybucyjnego](https://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
> Przed uzyskaniem dostępu do pakietu redystrybucyjnego izolowanej powłoki zostanie wyświetlony monit o wypełnienie krótkiej ankiety klienta.  Po wypełnieniu ankiety nastąpi przekierowanie do strony programu Visual Studio Connect z linkami pobierania pakietu redystrybucyjnego.  Linki do pobrania można znaleźć w kolejnych odwiedzinach w witrynie programu Visual Studio Connect w obszarze **programy &#124; Visual Studio 2015 Integrated i izolowana powłoka** .  
  
> [!NOTE]
> Aby uzyskać więcej informacji o sposobie wdrażania izolowanej aplikacji opartej na powłokach, zobacz [Przewodnik: Tworzenie podstawowej aplikacji powłoki izolowanej](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Praca z powłoką izolowaną  
 Aplikacja powłoki izolowanej programu Visual Studio ma pełny dostęp do usług Visual Studio i obsługuje specjalne Dostosowywanie i znakowanie. Istnieje kilka sposobów dostosowywania izolowanej aplikacji powłoki:  
  
- Można użyć części składników pakietów VSPackage i Managed Extensibility Framework (MEF), aby rozszerzać izolowaną aplikację powłoki tak samo jak w przypadku innych rozszerzeń programu Visual Studio. Aby uzyskać więcej informacji, zobacz [rozszerzanie izolowanej powłoki](../extensibility/extending-the-isolated-shell.md).  
  
- Aby umożliwić dostęp do funkcji i grup poleceń menu programu Visual Studio, zaktualizuj plik vsct w projekcie interfejsu użytkownika aplikacji.  
  
- Aby usunąć strony **opcji** lub inne składniki programu Visual Studio Shell z aplikacji, zaktualizuj plik. pkgundef aplikacji.  
  
- Aby zmodyfikować inne aspekty wyglądu lub zachowania powłoki, zaktualizuj plik. pkgdef aplikacji.  
  
- Niektóre aspekty powłoki można także określić, gdy aplikacja jest uruchomiona. W tym celu należy zaktualizować parametry w wywołaniu punktu wejścia startowego Appenvstub. dll.  
  
  Aby uzyskać więcej informacji na temat różnych elementów, które można dostosować, zobacz [elementy powłoki izolowanej](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Standardowe funkcje powłoki izolowanej  
 Poniższe funkcje są standardowe dla wszystkich wersji programu Visual Studio.  
  
|Kategoria funkcji|Funkcja|  
|----------------------|-------------|  
|Funkcje środowiska IDE|Ustawienia importu/eksportu<br /><br /> Instalator kontrolki przybornika<br /><br /> Lista zadań & Lista błędów<br /><br /> Okno wyniku<br /><br /> Strona początkowa<br /><br /> Okno Właściwości<br /><br /> Przybornik<br /><br /> Eksplorator rozwiązań<br /><br /> Okno zakładek<br /><br /> Widok klas<br /><br /> Przeglądarka obiektów<br /><br /> Okno polecenia<br /><br /> Konspekt dokumentu<br /><br /> Widok zasobów<br /><br /> Narzędzie zewnętrzne<br /><br /> Dodaj odwołanie do usługi Windows Communication Foundation (WCF)<br /><br /> Obsługa zapytań języka Integrated Language (LINQ)|  
|Edytor/Projektant|Narzędzia do przeglądania kodu (ujednolicone Znajdowanie, definicja źródła, dziedziczenie)<br /><br /> IntelliSense<br /><br /> SmartTags<br /><br /> Menedżer fragmentów kodu<br /><br /> Wstawki kodu<br /><br /> Refaktoryzacja<br /><br /> Łatwa lista<br /><br /> Filtrowanie IntelliSense<br /><br /> Okno definicji kodu<br /><br /> projektant aplikacji<br /><br /> Projektant Windows Forms<br /><br /> Projektant Windows Presentation Foundation (WPF)|  
|Debugowanie|C#Ewaluatora wyrażeń<br /><br /> Debugowanie lokalne<br /><br /> Debugowanie zarządzane<br /><br /> Edytuj i kontynuuj<br /><br /> Debugowanie między wątkami<br /><br /> Wizualizacje<br /><br /> DataTips<br /><br /> Debugowanie natywne<br /><br /> Debugowanie skryptów<br /><br /> Debugowanie międzyoperacyjności<br /><br /> Debugowanie just-in-Time (JIT)<br /><br /> Debugowanie wieloprocesowe<br /><br /> Debugowanie kodu XSLT<br /><br /> Dołącz do procesu lokalnego<br /><br /> Punkty śledzenia<br /><br /> Ograniczenia punktów przerwania|  
|Dane|Eksplorator serwera (tylko dane uproszczone)<br /><br /> Dane są powiązane z danymi lokalnymi (. MDF lub. MDB<br /><br /> Powiązanie danych z obiektem<br /><br /> Powiązanie danych z usługą sieci Web<br /><br /> Pełny zestaw kontrolek danych<br /><br /> Edytor XML<br /><br /> Powiązanie danych z lokalnym serwerem baz danych<br /><br /> Data Sources — Okno|  
|sieć Web|Edytor HTML<br /><br /> Przeglądarki sieci Web<br /><br /> Projektant formularzy sieci Web<br /><br /> Projekt witryny sieci Web<br /><br /> Projekt aplikacji sieci Web|  
|Rozszerzalność|Używa składników pakietów VSPackage i MEF|  
  
## <a name="see-also"></a>Zobacz też  
 [Shell (Isolated lub Integrated)](../extensibility/shell-isolated-or-integrated.md)
