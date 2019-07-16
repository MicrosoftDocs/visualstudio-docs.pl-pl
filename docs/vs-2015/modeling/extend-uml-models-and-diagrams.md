---
title: Rozszerzanie modeli i diagramów UML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 917c88056709cfbeb89ce3f19d9c8da9866feb4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182862"
---
# <a name="extend-uml-models-and-diagrams"></a>Rozszerzanie modeli i diagramów UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat zawiera podsumowanie różnych sposobów, w którym można rozszerzyć narzędzi dostępnych w programie Visual Studio do modelowania UML. Aby dowiedzieć się, które wersje programu Visual Studio obsługują każdego typu modelu i narzędzia, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 W poniższym przykładowym scenariuszu Fabrikam projektuje i instaluje bagażu Kuwejcie obsługi systemów. Z Kuwejcie jednego projektu do następnego istnieje wiele podobieństw podstawowy sprzęt i oprogramowanie, które kontroluje ją. Istnieją jednak również kilka czynników, które są bardzo zróżnicowane, takie jak konfiguracja poziome, działami zaewidencjonowania, silosów i innych pakiet obsługi urządzeń.  
  
 Przy rozpoczynaniu nowego projektu, zespół firmy Fabrikam tworzy modelu UML, aby pomóc im omówiono wymagania w zakresie między sobą oraz z ich odbiorcą. Diagramy aktywności ich używać do reprezentowania przepływ zbiory, z węzłami obiekt reprezentujący na każdym urządzeniu. UML model nie reprezentuje bezpośrednio kodu systemowego.  
  
 Fabrikam narzędzia team sprawia, że szereg ulepszeń, aby pomóc zespołom programistycznym. W poniższych sekcjach opisano różne rodzaje rozszerzeń, które można zdefiniować. Niektóre z tych metod można łączyć w jedno rozszerzenie programu Visual Studio.  
  
 Aby uzyskać więcej informacji, zobacz ten film wideo: ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo")[MSDN jak mogę serii: Narzędzia UML i rozszerzalność](http://go.microsoft.com/fwlink/?LinkId=214467).  
  
## <a name="Requirements"></a> Wymagania  
  
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
- [Modeling SDK for Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=48148).  
  
## <a name="profiles"></a>Profile  
 Profile umożliwiają definiowanie stereotypów i dodatkowe właściwości dla elementów UML.  
  
 Fabrikam projektantów narzędzi zdefiniować stereotypy dla węzłów obiektowych diagramów działanie, takie jak "taśmy taśmy" i "checkin technicznej". Gdy członek zespołu tworzy bagażu, obsługa schematu za pomocą diagramu aktywności, mogą teraz ustawiać stereotypów, aby wskazać, jakiego rodzaju urządzenia, które reprezentuje każdego węzła. Deweloperom narzędzia do definiowania dodatkowych właściwości na niektórych stereotypów, dzięki czemu użytkownicy mogą rejestrować wartości, takich jak pojemność taśmy taśmy i skrętności dla działu zaewidencjonowania.  
  
 Aby uzyskać więcej informacji, zobacz [Definiowanie profilu w celu rozszerzenia UML](../modeling/define-a-profile-to-extend-uml.md).  
  
## <a name="custom-toolbox-items"></a>Elementy do przybornika niestandardowego  
 Element przybornika niestandardowego tworzy element lub grupę elementów na podstawie prototypu, który zdefiniujesz na diagramie. Na przykład można utworzyć narzędzie, które tworzy przypadki użycia określonego koloru, stereotyp lub grupę klas i skojarzenia, które stanowi wzorca projektowego. Można dodać te elementy przybornika do rozszerzenia programu Visual Studio i rozdystrybuować je innym użytkownikom.  
  
 Aby uzyskać więcej informacji, zobacz [Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
## <a name="validation"></a>Walidacja  
 Można zdefiniować reguły, aby upewnić się, że UML model spełnia określone ograniczenia.  
  
 Fabrikam narzędzie deweloperów zdefiniować reguły, aby pomóc członkom zespołu uniknąć błędów proste w obsłudze modeli bagażu. Na przykład działu zaewidencjonowania nie można podłączyć bezpośrednio do zasobnika magazynu. Musi istnieć przynajmniej taśma taśmy między nimi.  
  
 Aby uzyskać więcej informacji, zobacz [definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
## <a name="menu-commands"></a>Polecenia menu  
 Można zdefiniować polecenia, które użytkownicy mogą być wywoływane przez kliknięcie prawym przyciskiem myszy elementy na UML diagram. Polecenia można zaktualizować modelu i diagramów lub wykonywać inne operacje w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
 Firma Fabrikam definiuje polecenia menu, aby automatyzować często wykonywane operacje takie jak Utwórz technicznej ewidencjonowania i połącz go z taśmy wybrane taśmy lub zmienić układ diagramu zgodnie z regułami układu firmy.  
  
 Zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="gestures"></a>Gestów  
 Można zdefiniować polecenia, które użytkownicy inicjują przez dwukrotne kliknięcie elementu diagramu lub przeciągając do diagramu lub elementu na diagramie. Można zdefiniować polecenia, które mogą dotyczyć elementy przeciągnięte z innych diagramów UML z innymi częściami programu Visual Studio lub z innych aplikacji lub Eksploratora Windows (lub Eksploratora plików.  
  
 Członkowie zespołu Fabrikam można skojarzyć plików, takich jak specyfikację z dowolnego elementu modelu, przeciągając go z pulpitu Windows. Projektantów narzędzi definicja stereotypu, która zapewnia dowolnego elementu z właściwością ścieżkę pliku i gest, który ustawia stereotyp i ścieżkę pliku, gdy plik zostanie upuszczony na element.  
  
 Aby uzyskać więcej informacji, zobacz [definiowanie procedury obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).  
  
## <a name="responding-to-changes"></a>Reagowanie na zmiany  
 Czy przyczyną akcji użytkownika lub innego kodu programu, można napisać kod, który odpowiada na zmiany w modelu.  
  
 Fabrikam deweloperom tworzenie kodu, który automatycznie ustawia zależne od stereotypie kolor elementu. Dzięki temu można łatwo dla użytkowników odróżnić różne role pełnione przez elementy w modelach.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Odpowiadanie na zmiany w modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).  
  
## <a name="model-bus"></a>Model Bus  
 Model Bus pozwala na dostęp na diagramie lub modelu z innego diagramu lub z innego [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozszerzenia. Między innymi umożliwia to informacje rozkłada się na więcej niż jednego modelu kilka osób może pracować na połączone modelu, w tym samym czasie.  
  
 Firma Fabrikam korzysta elementów na diagramach aktywności do reprezentowania bagażu obsługi urządzenia. Każdy element urządzenia mogą mieć bardziej szczegółowe specyfikacji w innego diagramu, który może być inny model. Ograniczenia sprawdzania poprawności na diagramie przepływu bagażu może pobrać odpowiednie właściwości urządzenia z innych diagramów. Odwołania z innymi diagramami są przechowywane w dodatkowych właściwości zdefiniowane w stereotypów.  
  
 Aby uzyskać więcej informacji, zobacz [modeli UML, integracja z innymi modelami i narzędziami](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
## <a name="generation"></a>Generowanie  
 Z modelu można wygenerować kodu programu, skrypty, konfiguracje, dokumenty, nowe modele lub inne artefakty.  
  
 W systemach bagażu, które projekty firmy Fabrikam większość kodu programu jest taka sama, z poziomu jednego projektu do drugiego. Główne aspektem zmiennej jest planu przepływu bagażu wokół port. Po zespół projektowy miał możliwości ich pierwsze kilka projektów, projektantów narzędzi utworzyć szablon, który generuje z modelem bagażu przepływ dużej ilości kodu zmiennej programu i innych plików, takich jak dokumenty użytkownika. Znacznie zmniejsza czas i błąd wskaźnik rozwoju dla każdego nowego projektu.  
  
 Aby uzyskać więcej informacji, zobacz [Generowanie plików z modelu UML](../modeling/generate-files-from-a-uml-model.md).  
  
## <a name="team-foundation-server-integration"></a>Integracja z Team Foundation Server  
 Możesz łączyć elementy robocze z elementami modelu i programowy dostęp do połączonych elementów.  
  
 Programiści narzędzie Fabrikam pisać narzędziem, które generuje harmonogram pracy dla każdego projektu lotniczego. Elementy robocze w harmonogramie są połączone z elementami modelu.  
  
 Aby uzyskać więcej informacji, zobacz [definiowanie procedury obsługi łącza elementu roboczego](../modeling/define-a-work-item-link-handler.md).  
  
## <a name="tools-that-update-models"></a>Narzędzia, które aktualizują modeli  
 Można tworzyć aplikacje autonomiczne i rozszerzenia programu Visual Studio, które można załadować modeli UML.  
  
 Fabrikam deweloperom tworzenie narzędzi, który odczytuje model i generuje raporty z postępu prac dla każdego elementu modelu.  
  
 Aby uzyskać więcej informacji, zobacz [odczytywanie modelu UML w kodzie programu](../modeling/read-a-uml-model-in-program-code.md).  
  
## <a name="domain-specific-languages"></a>Języki specyficzne dla domeny  
 W przypadku, gdy używasz często określonego typu modelu, może być przydatne do tworzenia języka specyficznego dla domeny. To jest możliwe do własnych potrzeb biznesowych dokładniej modelu UML, ale wymaga więcej nakładu pracy, można ją skompilować i obsługiwać. Aby uzyskać więcej informacji, zobacz [zestawu Modeling SDK for Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
|**Kategoria**|**Łącza**|  
|------------------|---------------|  
|**Filmy wideo**|![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo") [MSDN jak mogę serii: Narzędzia UML i rozszerzalność](http://go.microsoft.com/fwlink/?LinkId=214467)<br /><br /> ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo") [witryny Channel 9: UML w programie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=199957)|  
|**Fora**|-   [Program Visual Studio visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Program Visual Studio visualization and Modeling SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogi**|[Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Artykuły techniczne i dzienniki**|[Centrum MSDN architektury](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)   
 [Wykaz interfejsów API dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
