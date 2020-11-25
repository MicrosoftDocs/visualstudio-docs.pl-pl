---
title: Zagadnienia dotyczące rozwiązania w trybie piaskownicy | Microsoft Docs
description: Poznaj rozwiązania w trybie piaskownicy, które są funkcją w programie Microsoft SharePoint, która umożliwia użytkownikom kolekcji witryn przekazywanie własnych niestandardowych rozwiązań kodu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 17b310a3f992f80b04ad14bb6e038e05b009a4af
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970467"
---
# <a name="sandboxed-solution-considerations"></a>Zagadnienia dotyczące rozwiązania w trybie piaskownicy
  *Rozwiązania w trybie piaskownicy* to funkcja programu Microsoft SharePoint 2010, która umożliwia użytkownikom kolekcji witryn przekazywanie własnych niestandardowych rozwiązań kodu. Typowym rozwiązaniem w trybie piaskownicy jest przekazywanie własnych składniki Web Part.

 Aplikacja SharePoint w trybie piaskownicy działa w bezpiecznym, monitorowanym procesie, który ma dostęp do ograniczonej części kolektywu serwerów sieci Web. Program Microsoft SharePoint 2010 używa kombinacji funkcji, galerii rozwiązań, monitorowania rozwiązań i struktury sprawdzania poprawności, aby umożliwić korzystanie z rozwiązań w trybie piaskownicy.

## <a name="specify-project-trust-level"></a>Określ poziom zaufania projektu
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsługuje rozwiązania w trybie piaskownicy za pomocą logicznej właściwości projektu o nazwie *rozwiązanie w trybie piaskownicy*. Tę właściwość można ustawić w dowolnym momencie w projekcie lub można ją określić podczas tworzenia projektu w **Kreatorze dostosowywania programu SharePoint**.

> [!NOTE]
> Zmiana właściwości *rozwiązania w trybie piaskownicy* po utworzeniu projektu może spowodować błędy walidacji.

 Rozwiązanie jest uznawane za rozwiązanie w zakresie farmy, jeśli właściwość *rozwiązanie w trybie piaskownicy* ma **wartość FAŁSZ** lub wybrano opcję **Wdróż jako farmę** . Jednak rozwiązanie jest traktowane inaczej niż rozwiązanie farmy, jeśli właściwość rozwiązanie w *trybie piaskownicy* ma **wartość true** lub wybrano opcję **Wdróż jako rozwiązanie w trybie piaskownicy** w kreatorze.

## <a name="sharepoint-site-hierarchy"></a>Hierarchia witryny programu SharePoint
 Aby zrozumieć, jak działają rozwiązania w trybie piaskownicy, warto wiedzieć, że witryny programu SharePoint są hierarchiczne w zakresie. Element Top jest znany jako Farma sieci Web, a inne elementy są podrzędne:

 Farma sieci Web

 Aplikacja sieci Web A

 Zbiór witryn a1

 A1A lokacji

 Aplikacja sieci Web B

 Zbiór witryn B1

 B1a lokacji

 B1b lokacji

 Zbiór witryn B2

 B2A lokacji

 Jak widać, farmy serwerów sieci Web mogą zawierać co najmniej jedną aplikację sieci Web, która z kolei może zawierać co najmniej jedną kolekcję witryn, która może mieć lokacje podrzędne i tak dalej. Zmiany wprowadzone w jednym zbiorze witryn mają wpływ tylko na zbiór witryn i inne. Zmiany wprowadzone na poziomie farmy sieci Web mają jednak wpływ na wszystkie zbiory witryn w farmie.

 Program Windows SharePoint Services (WSS) 3,0 umożliwia wdrażanie rozwiązań tylko na poziomie farmy, ale pozwala na [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] wdrożenie na poziomie farmy (rozwiązanie farmy) lub na poziomie zbioru witryn (rozwiązanie w trybie piaskownicy).

## <a name="why-sandboxed-solutions"></a>Dlaczego warto korzystać z rozwiązań w trybie piaskownicy?
 W programie WSS 3,0 rozwiązania mogą być wdrażane tylko na poziomie farmy. Oznacza to, że możliwe jest wdrożenie potencjalnie szkodliwych lub destabilizujących rozwiązań, które mają wpływ na całą farmę sieci Web i wszystkie inne kolekcje witryn i aplikacje, które działają w ramach tego programu. Jednak korzystając z rozwiązań w trybie piaskownicy, można wdrożyć rozwiązania w podobszarze farmy, w określonej kolekcji witryn. Aby zapewnić dodatkową ochronę, zestaw rozwiązania nie jest ładowany do [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] procesu głównego (*w3wp.exe*). Zamiast tego jest ładowany do osobnego procesu (*SPUCWorkerProcess.exe*). Ten proces jest monitorowany i implementuje limity przydziału i ograniczania przepustowości w celu ochrony farmy przed rozwiązaniami w trybie piaskownicy, które wykonują szkodliwe działania, na przykład uruchamiając ścisłe pętle korzystające z cykli procesora CPU.

## <a name="site-collection-solution-gallery"></a>Galeria rozwiązań kolekcji witryn
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 zawiera funkcję, która jest znana jako "Galeria rozwiązań kolekcji witryn". Możesz uzyskać dostęp do tej funkcji na stronie administracji centralnej programu SharePoint 2010 lub otwierając menu **Akcje lokacji** , wybierając pozycję **Ustawienia lokacji**, a następnie wybierając łącze **rozwiązania** w obszarze  **Galerie** w witrynie programu SharePoint. Galerie rozwiązań to repozytoria rozwiązań, które umożliwiają administratorom zbioru witryn zarządzanie rozwiązaniami w ich kolekcjach witryn.

 Galeria rozwiązań jest biblioteką dokumentów przechowywaną w głównej sieci Web witryny programu SharePoint. Galeria rozwiązań zastępuje szablony witryn i obsługuje pakiety rozwiązań. Gdy przekazywany jest plik pakietu rozwiązania programu SharePoint (*wsp*), jest on przetwarzany jako rozwiązanie w trybie piaskownicy.

## <a name="sandboxed-solution-limitations"></a>Ograniczenia rozwiązania w trybie piaskownicy
 Po wdrożeniu rozwiązania w trybie piaskownicy dostępna jest tablica funkcji programu SharePoint, która może pomóc w ograniczeniu wszelkich luk w zabezpieczeniach. Poniżej wymieniono niektóre z tych ograniczeń:

- Rozwiązania w trybie piaskownicy mają ograniczony podzestaw dostępnych elementów rozwiązania do wdrożenia. Potencjalnie podatne na ataki szablony projektów programu SharePoint, takie jak definicje witryn i przepływy pracy, są niedostępne.

- Program SharePoint uruchamia kod rozwiązania w trybie piaskownicy w procesie (*SPUCWorkerProcess.exe*) oddzielonym od [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] procesu głównej puli aplikacji (*w3wp.exe*).

- Zamapowane foldery nie mogą zostać dodane do projektu.

- Typów w [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] zestawie Microsoft. Office. Server nie można używać w rozwiązaniach w trybie piaskownicy. Ponadto [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] w rozwiązaniach w trybie piaskownicy można używać tylko typów w zestawie Microsoft. SharePoint.

  Należy pamiętać, że określenie rozwiązania programu SharePoint jako rozwiązania w trybie piaskownicy nie ma wpływu na serwer programu SharePoint; Określa on tylko, w jaki sposób projekt programu SharePoint jest wdrażany w programie SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i jakie zespoły są do nich powiązane. Nie ma to wpływu na wygenerowany plik *. wsp* , a plik *. wsp* nie zawiera danych, które są bezpośrednio skorelowane z właściwością *rozwiązania w trybie piaskownicy* .

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Możliwości i elementy w rozwiązaniach w trybie piaskownicy
 Rozwiązania w trybie piaskownicy obsługują następujące możliwości i elementy:

- Typy zawartości/pola

- Akcje niestandardowe

- Deklaratywne przepływy pracy

- Odbiorcy zdarzeń

- Objaśnienia funkcji

- Definicje list

- Wystąpienia listy

- Moduł/pliki

- Nawigacja

- *Onet.xml*

- SPItemEventReceiver

- SPListEventReceiver

- SPWebEventReceiver

- Obsługa wszystkich składniki Web Part pochodzących od `System.Web.UI.WebControls.WebParts.WebPart`

- Części sieci Web

- Elementy funkcji szablonu webtemplate (zamiast *Webtemp.xml*)

- składniki Web Part wizualizacji

  Rozwiązania w trybie piaskownicy nie obsługują następujących możliwości i elementów:

- Strony aplikacji

- Niestandardowa grupa akcji

- Funkcje w zakresie farmy

- `HideCustomAction`, element

- Funkcje w zakresie aplikacji sieci Web

- Przepływy pracy z kodem

## <a name="see-also"></a>Zobacz też
- [Różnice między rozwiązaniami w trybie piaskownicy a farmą](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
