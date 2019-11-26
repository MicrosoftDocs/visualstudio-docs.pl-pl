---
title: Rozszerzając modele i diagramy UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b8b154ccd18472d0b0bca502c78a6612aeccdda6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301046"
---
# <a name="extend-uml-models-and-diagrams"></a>Rozszerzanie modeli i diagramów UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat zawiera podsumowanie różnych sposobów, w których można rozłożyć narzędzia modelowania UML dołączone do programu Visual Studio. Aby sprawdzić, które wersje programu Visual Studio obsługują każdy typ modelu i narzędzie, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 W poniższym przykładowym scenariuszu firma Fabrikam projektuje i instaluje systemy obsługi bagażu na lotnisku. Z jednego projektu lotniska do następnego istnieje wiele podobieństw w podstawowym sprzęcie i oprogramowaniu, które je kontroluje. Istnieją jednak również różne czynniki, które różnią się od siebie, takie jak konfiguracja pasów przenośnika, działy zaewidencjonowania, pojemniki do magazynowania i inne urządzenia obsługujące worek.

 Podczas uruchamiania nowego projektu zespół firmy Fabrikam tworzy model UML, który pomoże im omawiać te wymagania między sobą i klientem. Wykorzystują one diagramy aktywności do reprezentowania przepływu toreb, z węzłami obiektów reprezentującymi każdy sprzęt. Model UML nie reprezentuje bezpośrednio kodu systemu.

 Zespół narzędzi firmy Fabrikam wprowadza szereg ulepszeń, które ułatwiają zespołom programistycznym. W poniższych sekcjach opisano różne rodzaje rozszerzeń, które można zdefiniować. Niektóre z tych technik można połączyć w jedno rozszerzenie programu Visual Studio.

 Aby uzyskać więcej informacji, zobacz ten film wideo: ![link do filmu wideo](../data-tools/media/playvideo.gif "PlayVideo")[MSDN — jak to zrobić: narzędzia i rozszerzalność UML](https://go.microsoft.com/fwlink/?LinkId=214467).

## <a name="Requirements"></a>Wymagania

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

- [Modeling SDK dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148).

## <a name="profiles"></a>Profil
 Profile umożliwiają definiowanie stereotypów i dodatkowych właściwości elementów UML.

 Deweloperzy narzędzi firmy Fabrikam definiują stereotypy obiektów w węzłach diagramów aktywności, takich jak «taśma przenośnika» i «punkt zaewidencjonowania. Gdy członek zespołu tworzy schemat obsługi bagażu przy użyciu diagramu aktywności, można teraz ustawić stereotypy, aby wskazać typ wyposażenia reprezentowanego przez każdy węzeł. Deweloperzy narzędzi definiują dodatkowe właściwości niektórych stereotypów, dzięki czemu użytkownicy mogą rejestrować wartości, takie jak pojemność taśmy przenośnika i skrętności.

 Aby uzyskać więcej informacji, zobacz [Definiowanie profilu do rozszerania UML](../modeling/define-a-profile-to-extend-uml.md).

## <a name="custom-toolbox-items"></a>Niestandardowe elementy przybornika
 Niestandardowy element przybornika tworzy element lub grupę elementów ze prototypu zdefiniowanego w diagramie. Można na przykład utworzyć narzędzie, które tworzy przypadki użycia w określonym kolorze lub stereotypie, lub grupę klas i skojarzeń, które reprezentują Wzorzec projektowy. Można dodać te elementy przybornika do rozszerzeń programu Visual Studio i przekazać je innym użytkownikom.

 Aby uzyskać więcej informacji, zobacz [Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md).

## <a name="validation"></a>Walidacja
 Można zdefiniować reguły, aby upewnić się, że model UML jest zgodny z określonymi ograniczeniami.

 Deweloperzy narzędzi firmy Fabrikam definiują reguły ułatwiające członkom zespołu uniknięcie prostych pomyłek w modelach obsługi bagażu. Na przykład punkt zaewidencjonowania nie może zostać połączony bezpośrednio z bin magazynu. Między nimi musi być przynajmniej taśma przenośnika.

 Aby uzyskać więcej informacji, zobacz [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="menu-commands"></a>Polecenia menu
 Można definiować polecenia, które użytkownicy mogą wywoływać przez kliknięcie prawym przyciskiem myszy elementów na diagramie UML. Polecenia mogą aktualizować model i diagramy lub wykonywać inne operacje w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

 Firma Fabrikam definiuje polecenia menu do automatyzowania często wykonywanych operacji, takich jak tworzenie biurka zaewidencjonowania i łączenie go z wybranym taśmą przenośnika lub zmiana rozmieszczenia diagramu zgodnie z regułami układu firmy.

 Zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

## <a name="gestures"></a>Gestów
 Można definiować polecenia inicjowane przez użytkowników przez dwukrotne kliknięcie elementu diagramu lub przeciągnięcie go na diagram lub element na diagramie. Można definiować polecenia, które mogą odnosić się do elementów przeciąganych z innych diagramów UML, z innych części programu Visual Studio lub z innych aplikacji lub Eksploratora Windows (lub Eksploratora plików).

 Członkowie zespołu Fabrikam mogą skojarzyć plik, taki jak specyfikacja z dowolnym elementem modelu, przeciągając go z pulpitu systemu Windows. Deweloperzy narzędzi zdefiniowali stereotyp, który zapewnia dowolny element z właściwością Path pliku oraz gest ustawiający stereotyp i ścieżkę pliku, gdy plik zostanie upuszczony do elementu.

 Aby uzyskać więcej informacji, zobacz [Definiowanie obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).

## <a name="responding-to-changes"></a>Reagowanie na zmiany
 Można napisać kod, który reaguje na zmiany w modelu, niezależnie od tego, czy jest to spowodowane przez akcje użytkownika, czy przez inny kod programu.

 Deweloperzy firmy Fabrikam tworzą kod, który automatycznie ustawia kolor elementu zależnego od jego stereotypu. Dzięki temu użytkownicy mogą łatwo rozróżnić różne role odtwarzane przez elementy w modelach.

 Aby uzyskać więcej informacji, zobacz [How to: reagować na zmiany w modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).

## <a name="model-bus"></a>Magistrala modelu
 Model Bus umożliwia dostęp do diagramu lub modelu z innego diagramu lub z innego rozszerzenia [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Dzięki temu można rozłożyć informacje między różnymi modelami, dzięki czemu kilka osób może pracować nad połączonym modelem w tym samym czasie.

 Firma Fabrikam używa elementów na diagramach aktywności do reprezentowania sprzętu obsługującego bagaż. Każdy element sprzętu może mieć bardziej szczegółową specyfikację w innym diagramie, który może znajdować się w innym modelu. Ograniczenia walidacji na diagramie przepływu bagażu mogą pobrać odpowiednie właściwości sprzętu z innych diagramów. Odwołania do innych diagramów są przechowywane we właściwościach dodatkowych zdefiniowanych w stereotypach.

 Aby uzyskać więcej informacji, zobacz [integrowanie modeli UML z innymi modelami i narzędziami](../modeling/integrate-uml-models-with-other-models-and-tools.md).

## <a name="generation"></a>Generacji
 Z modelu można generować kod programu, skrypty, konfiguracje, dokumenty, nowe modele lub inne artefakty.

 W systemach bagażowych, które są projektami firmy Fabrikam, większość kodu programu jest taka sama z jednego projektu do następnego. Aspekt zmiennej głównej to plan przepływu bagażu wokół lotniska. Gdy zespół projektowy osiągnął doświadczenie z kilku pierwszych projektów, deweloperzy narzędzi tworzą szablon generujący, w modelu przepływu bagażu, większość kodu programu zmiennej i innych plików, takich jak dokumenty użytkownika. Znacznie skraca to czas projektowania i częstotliwość błędów dla każdego nowego projektu.

 Aby uzyskać więcej informacji, zobacz [generowanie plików z modelu UML](../modeling/generate-files-from-a-uml-model.md).

## <a name="team-foundation-server-integration"></a>Integracja Team Foundation Server
 Można łączyć elementy robocze z elementami modelu i programistycznie uzyskiwać dostęp do połączonych elementów.

 Deweloperzy narzędzi firmy Fabrikam piszą narzędzie generujące harmonogram pracy dla każdego projektu lotniska. Elementy robocze w harmonogramie są połączone z elementami modelu.

 Aby uzyskać więcej informacji, zobacz [Definiowanie procedury obsługi łącza elementu pracy](../modeling/define-a-work-item-link-handler.md).

## <a name="tools-that-update-models"></a>Narzędzia, które aktualizują modele
 Można tworzyć aplikacje autonomiczne i rozszerzenia programu Visual Studio, które mogą ładować modele UML.

 Deweloperzy firmy Fabrikam tworzą narzędzie, które odczytuje model i generuje raporty o postępie pracy dla każdego elementu modelu.

 Aby uzyskać więcej informacji, zobacz [Odczytywanie modelu UML w kodzie programu](../modeling/read-a-uml-model-in-program-code.md).

## <a name="domain-specific-languages"></a>Języki specyficzne dla domeny
 Często używany typ modelu może być przydatny do tworzenia języka specyficznego dla domeny. Można to zrobić, aby dopasować się do potrzeb firmy w sposób bardziej ścisły niż model UML, ale wymaga większego wysiłku, aby go skompilować i zachować. Aby uzyskać więcej informacji, zobacz [Modeling SDK for Visual Studio — Języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategorii**|**Linki**|
|------------------|---------------|
|**Filmy wideo**|![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") [MSDN: jak serie — narzędzia i rozszerzalność UML](https://go.microsoft.com/fwlink/?LinkId=214467)<br /><br /> ![link do kanału wideo](../data-tools/media/playvideo.gif "PlayVideo") [9: UML z programem Visual Studio](https://go.microsoft.com/fwlink/?LinkId=199957)|
|**Dotyczące**|-   [Wizualizacja programu Visual Studio & narzędzia do modelowania](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [wizualizacji programu Visual Studio & Modeling SDK (narzędzia DSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogi**|[Blog programu Visual Studio ALM + Team Foundation Server](https://go.microsoft.com/fwlink/?LinkID=201340)|
|**Artykuły techniczne i dzienniki**|[Centrum architektury MSDN](https://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Zobacz też
 [Utwórz modele dla](../modeling/create-models-for-your-app.md) [dokumentacji interfejsu API aplikacji dla ROZSZERZALNości modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
