---
title: Uwagi dotyczące rozwiązania typu piaskownica | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 28bdf4e9b116522256606bc9fbbe6b05edb45114
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872979"
---
# <a name="sandboxed-solution-considerations"></a>Uwagi dotyczące rozwiązania typu piaskownica
  *Rozwiązania piaskownicy* to funkcja programu Microsoft SharePoint 2010, umożliwiająca użytkownikom kolekcji witryny do przekazania własnych rozwiązań kodu niestandardowego. Typowe rozwiązanie w trybie piaskownicy jest użytkownikom przekazywanie własnych składników Web Part.  
  
 Aplikacja w trybie piaskownicy programu SharePoint działa w bezpiecznym, monitorowanym procesie, który ma dostęp do ograniczonej częścią kolektywu serwerów sieci Web. Program Microsoft SharePoint 2010 używa kombinacji funkcji, galerie rozwiązania, rozwiązanie monitorowania i szablon sprawdzania poprawności, aby umożliwić rozwiązania w trybie piaskownicy.  
  
## <a name="specify-project-trust-level"></a>Określ poziom zaufania projektu
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsługuje rozwiązania w trybie piaskownicy za pomocą właściwości projektu logiczną o nazwie *rozwiązanie w trybie piaskownicy*. Tę właściwość można ustawić w dowolnym momencie w projekcie lub można określić, podczas tworzenia projektu w **Kreator ustawień niestandardowych SharePoint**.  
  
> [!NOTE]  
>  Zmiana *rozwiązanie w trybie piaskownicy* właściwość projektu po jego utworzeniu może spowodować błędy sprawdzania poprawności.  
  
 To rozwiązanie jest uznawana za rozwiązania z zakresu farmy, jeśli *rozwiązanie w trybie piaskownicy* właściwość jest ustawiona na **false** lub można wybrać **Wdróż jako rozwiązanie farmy** opcji. Jednak rozwiązanie jest traktowany inaczej w rozwiązaniu farmy *rozwiązanie w trybie piaskownicy* właściwość jest ustawiona na **true** lub można wybrać **Wdróż jako rozwiązanie w trybie piaskownicy** Opcja w kreatorze.  
  
## <a name="sharepoint-site-hierarchy"></a>Hierarchia lokacji programu SharePoint
 Aby zrozumieć, jak w trybie piaskownicy rozwiązań pracę, warto wiedzieć, że witryn programu SharePoint są hierarchiczne w zakresie. Górnego elementu jest znany jako kolektywu serwerów sieci Web i inne elementy są podrzędne w stosunku do niego:  
  
 Kolektywu serwerów sieci Web  
  
 Aplikacja sieci Web A  
  
 A1 kolekcji witryny  
  
 A1a lokacji  
  
 Aplikacja sieci Web B  
  
 B1 kolekcji witryny  
  
 B1a lokacji  
  
 B1b lokacji  
  
 B2 kolekcji witryny  
  
 B2a lokacji  
  
 Jak widać, farmy serwerów sieci Web mogą zawierać jedną lub więcej aplikacji sieci Web, które z kolei może zawierać jedną lub więcej kolekcji witryny, które mogą mieć Lokacje podrzędne i tak dalej. Zmiany wykonane na jednej lokacji kolekcji wpływ tylko zbioru witryn i żadne inne. Zmiany wprowadzone na poziomie farmy sieci Web wpływa jednak na wszystkich zbiorach witryn w farmie.  
  
 Windows SharePoint Services (WSS) 3.0 pozwala wdrażać rozwiązania tylko na poziomie farmy, ale [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] służy do wdrażania na poziomie farmy (rozwiązanie farmy) lub poziom zbioru witryn (rozwiązanie w trybie piaskownicy).  
  
## <a name="why-sandboxed-solutions"></a>Dlaczego rozwiązania w trybie piaskownicy?
 W grupie WSS 3.0 rozwiązania można wdrożyć tylko na poziomie farmy. Oznacza to, że potencjalnie szkodliwego lub destabilizujące rozwiązania można wdrożyć, których to dotyczy całego kolektywu serwerów sieci Web i wszystkich zbiorach witryn i innych aplikacji działających w nim. Jednak za pomocą rozwiązania w trybie piaskownicy, można wdrożyć rozwiązania do podobszaru farmy kolekcji określonej lokacji. Aby zapewnić dodatkową ochronę, zestaw rozwiązania nie jest ładowany do głównej [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] procesu (*w3wp.exe*). Zamiast tego jest on ładowany w oddzielnym procesie (*SPUCWorkerProcess.exe*). Ten proces jest monitorowana i implementuje limity przydziału i ograniczanie przepustowości, aby chronić farmę z rozwiązania, które wykonują szkodliwe działania, takie jak uruchomienie ścisłej pętli, które zużywają cykle procesora CPU w trybie piaskownicy.  
  
## <a name="site-collection-solution-gallery"></a>Galeria rozwiązań zbioru witryn
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 korzystają z funkcji, który jest znany jako "lokacji kolekcji galerii rozwiązań." Możesz korzystać z tej funkcji ze strony administracji centralnej programu SharePoint 2010 lub otwierając **Akcje witryny** menu, wybierając **ustawienia lokacji**, a następnie wybierając **rozwiązania** łącze w obszarze **galerie** w witrynie programu SharePoint. Galerie rozwiązania są repozytoriów rozwiązania umożliwiające Administratorzy zbioru witryn, zarządzać rozwiązaniami w zbiorach witryn.  
  
 Galeria rozwiązań jest przechowywany w katalogu głównym witryny programu SharePoint w sieci Web biblioteki dokumentów. Galeria rozwiązań zastępuje szablony witryn i obsługuje pakietów rozwiązania. Gdy pakietu rozwiązania programu SharePoint (*.wsp*) plik zostanie przekazany, jest on przetwarzany jako rozwiązanie w trybie piaskownicy.  
  
## <a name="sandboxed-solution-limitations"></a>Ograniczenia dotyczące rozwiązania typu piaskownica
 Po wdrożeniu rozwiązania w trybie piaskownicy tablicy dostępnych funkcji programu SharePoint jest ograniczona do zmniejszenia luk w zabezpieczeniach, które może mieć. Niektóre z tych ograniczeń następujące:  
  
- Rozwiązania w trybie piaskownicy ma ograniczony podzestaw elementów możliwych do wdrożenia rozwiązania dostępne dla nich. Potencjalnie zagrożone szablony projektów programu SharePoint, takich jak witryna definicje i przepływy pracy, nie są dostępne.  
  
- SharePoint działa kodu rozwiązania w trybie piaskownicy w procesie (*SPUCWorkerProcess.exe*) niezależnie od głównej [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] puli aplikacji (*w3wp.exe*) procesu.  
  
- Nie można dodać folderów mapowanych do projektu.  
  
- Typy w [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] zestawu Microsoft.Office.Server nie można używać w rozwiązania w trybie piaskownicy. Ponadto tylko w przypadku typów w [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] zestawu Microsoft.SharePoint mogą być używane w trybie piaskownicy rozwiązań.  
  
  Ważne jest, aby należy pamiętać, że określenie rozwiązania programu SharePoint jako rozwiązanie w trybie piaskownicy nie ma wpływu na serwerze programu SharePoint; Określa tylko sposób wdrażania projektu programu SharePoint do programu SharePoint z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i jakie zestawy powiąże. Go nie ma wpływu na wygenerowany *.wsp* pliku i *.wsp* plik nie zawiera danych odpowiadająca bezpośrednio *rozwiązanie w trybie piaskownicy* właściwości.  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Funkcje i elementy w rozwiązania w trybie piaskownicy
 Rozwiązania piaskownicy obsługują następujące funkcje i elementy:  
  
- Typy zawartości/pól  
  
- Akcje niestandardowe  
  
- Deklaratywne przepływów pracy  
  
- Odbiorcy zdarzeń  
  
- Wywołania funkcji  
  
- Definicje list  
  
- Wystąpienia listy  
  
- Moduł i pliki  
  
- Nawigacja  
  
- *Onet.xml*  
  
- SPItemEventReceiver  
  
- SPListEventReceiver  
  
- SPWebEventReceiver  
  
- Obsługa wszystkich składników Web Part, które wynikają z `System.Web.UI.WebControls.WebParts.WebPart`  
  
- Części sieci Web  
  
- Elementów funkcji szablonu sieci Web (zamiast *Webtemp.xml*)  
  
- Wizualne części sieci Web  
  
  Rozwiązania piaskownicy nie obsługują następujące funkcje i elementy:  
  
- Strony aplikacji  
  
- Niestandardowe grupy akcji  
  
- Funkcji należących do zakresu farmy  
  
- `HideCustomAction` — element  
  
- Funkcje o zakresie aplikacji sieci Web  
  
- Przepływy pracy za pomocą kodu  
  
## <a name="see-also"></a>Zobacz także
 [Różnice między piaskownicy oraz rozwiązaniami farmy](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
