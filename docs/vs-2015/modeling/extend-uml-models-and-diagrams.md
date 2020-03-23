---
title: Rozszerzanie modeli i diagramów UML | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 7f4c490abbcd5b970c5bf9586ea881be4c5d62a4
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302330"
---
# <a name="extend-uml-models-and-diagrams"></a>Rozszerzanie modeli i diagramów UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie podsumowano różne sposoby rozszerzania narzędzi modelowania UML dołączonych do programu Visual Studio. Aby zobaczyć, które wersje programu Visual Studio obsługują każdy typ i narzędzie modelu, zobacz [Obsługa wersji dla architektury i narzędzi do modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 W poniższym scenariuszu przykładowym firma Fabrikam projektuje i instaluje systemy obsługi bagażu na lotnisku. Od jednego projektu lotniska do drugiego, istnieje wiele podobieństw w podstawowym sprzęcie i oprogramowaniu, które go kontroluje. Istnieje jednak również kilka czynników, które różnią się znacznie, takich jak konfiguracja taśm przenośnikowych, stanowisk odprawy, pojemników do przechowywania i innych urządzeń do transportu toreb.

 Podczas uruchamiania nowego projektu zespół fabrikam tworzy model UML, aby pomóc im omówić te wymagania między sobą i z klientem. Używają diagramów aktywności do reprezentowania przepływu worków, z węzłami obiektów reprezentującymi każdy element wyposażenia. Model UML nie reprezentuje bezpośrednio kodu systemu.

 Zespół narzędzi firmy Fabrikam wprowadza szereg ulepszeń, aby pomóc zespołom programistów. W poniższych sekcjach opisano różne rodzaje rozszerzeń, które można zdefiniować. Można połączyć kilka z tych technik w jedno rozszerzenie programu Visual Studio.

 Aby uzyskać więcej informacji, zobacz ten klip wideo: ![łącze do wideo](../data-tools/media/playvideo.gif "Wideo Play")[MSDN How Do I Series: UML Tools and Extensibility](https://msdn.microsoft.com/vstudio/ff859492).

## <a name="requirements"></a><a name="Requirements"></a>Wymagania

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

- [Modelowanie SDK dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148).

## <a name="profiles"></a>Profile
 Profile umożliwiają definiowanie stereotypów i dodatkowych właściwości elementów UML.

 Twórcy narzędzi firmy Fabrikam definiują stereotypy na węzłach obiektów diagramów aktywności, takich jak «przenośnik taśmowy» i «checkin desk». Gdy członek zespołu tworzy schemat obsługi bagażu przy użyciu diagramu aktywności, może teraz ustawić stereotypy, aby wskazać, jaki typ sprzętu reprezentuje każdy węzeł. Deweloperzy narzędzia definiują dodatkowe właściwości na niektórych stereotypach, dzięki czemu użytkownicy mogą rejestrować wartości, takie jak pojemność przenośnika taśmowego i ręczność stanowiska wyboru.

 Aby uzyskać więcej informacji, zobacz [Definiowanie profilu w celu rozszerzenia UML](../modeling/define-a-profile-to-extend-uml.md).

## <a name="custom-toolbox-items"></a>Niestandardowe elementy przybornika
 Element niestandardowego przybornika tworzy element lub grupę elementów z prototypu zdefiniowanego na diagramie. Na przykład można utworzyć narzędzie, które tworzy przypadki użycia w określonym kolorze lub stereotypie lub grupę klas i skojarzeń, która reprezentuje wzorzec projektu. Te elementy przybornika można dodać do rozszerzeń programu Visual Studio i rozpowszechniać je do innych użytkowników.

 Aby uzyskać więcej informacji, zobacz [Definiowanie elementu przybornika do modelowania niestandardowego](../modeling/define-a-custom-modeling-toolbox-item.md).

## <a name="validation"></a>Sprawdzanie poprawności
 Można zdefiniować reguły, aby upewnić się, że model UML jest zgodny z określonymi ograniczeniami.

 Twórcy narzędzi firmy Fabrikam definiują reguły, aby pomóc członkom zespołu uniknąć prostych błędów w modelach obsługi bagażu. Na przykład biurko zaewidencjonowania nie może być podłączone bezpośrednio do pojemnika do przechowywania. Musi istnieć przynajmniej przenośnik taśmowy między nimi.

 Aby uzyskać więcej informacji, zobacz [Definiowanie ograniczeń sprawdzania poprawności dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="menu-commands"></a>Polecenia menu
 Polecenia, które użytkownicy mogą wywoływać, można definiować, klikając prawym przyciskiem myszy elementy na diagramie UML. Polecenia mogą aktualizować model i diagramy lub [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]wykonywać inne operacje w programie .

 Fabrikam definiuje polecenia menu w celu zautomatyzowania często wykonywanych operacji, takich jak utworzenie stanowiska odprawy i podłączenie go do wybranego przenośnika taśmowego lub zmianę układu diagramu zgodnie z regułami układu firmy.

 Zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

## <a name="gestures"></a>Gestów
 Można zdefiniować polecenia inicjujące przez użytkowników, klikając dwukrotnie element diagramu lub przeciągając na diagram lub element na diagramie. Można zdefiniować polecenia, które mogą zajmować się elementami przeciąganymi z innych diagramów UML, z innych części programu Visual Studio lub z innych aplikacji lub Eksploratora Windows (lub Eksploratora plików.

 Członkowie zespołu firmy Fabrikam mogą skojarzyć plik, taki jak specyfikacja, z dowolnym elementem modelu, przeciągając go z pulpitu systemu Windows. Deweloperzy narzędzia zdefiniowane stereotyp, który zapewnia dowolny element z właściwości ścieżki pliku i gest, który ustawia stereotyp i ścieżkę pliku, gdy plik jest upuszczony na element.

 Aby uzyskać więcej informacji, zobacz [Definiowanie obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).

## <a name="responding-to-changes"></a>Reagowanie na zmiany
 Można napisać kod, który odpowiada na zmiany w modelu, czy spowodowane przez akcje użytkownika lub przez inny kod programu.

 Deweloperzy firmy Fabrikam tworzą kod, który automatycznie ustawia kolor elementu zależne od jego stereotypu. Ułatwia to użytkownikom odróżnienie różnych ról odgrywanych przez elementy w modelach.

 Aby uzyskać więcej informacji, zobacz [Jak: Odpowiadanie na zmiany w modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).

## <a name="model-bus"></a>Model magistrali
 Model magistrali umożliwia dostęp do diagramu lub [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] modelu z innego diagramu lub z innego rozszerzenia. Między innymi pozwala to na rozpowszechnianie informacji w więcej niż jednym modelu, dzięki czemu kilka osób może pracować nad połączonym modelem w tym samym czasie.

 Firma Fabrikam używa elementów na diagramach aktywności do reprezentowania sprzętu do obsługi bagażu. Każdy element wyposażenia może mieć bardziej szczegółową specyfikację na innym diagramie, który może być w innym modelu. Ograniczenia walidacji na diagramie przepływu bagażu mogą pobierać odpowiednie właściwości sprzętu z innych diagramów. Odwołania do innych diagramów są przechowywane w dodatkowych właściwości zdefiniowanych w stereotypach.

 Aby uzyskać więcej informacji, zobacz [Integrowanie modeli UML z innymi modelami i narzędziami](../modeling/integrate-uml-models-with-other-models-and-tools.md).

## <a name="generation"></a>Generowanie
 Z modelu można wygenerować kod programu, skrypty, konfiguracje, dokumenty, nowe modele lub inne artefakty.

 W systemach bagażu, które projektuje firma Fabrikam, większość kodu programu jest taka sama od jednego projektu do następnego. Głównym zmiennym aspektem jest plan przepływu bagażu wokół lotniska. Po tym, jak zespół projektowy miał doświadczenie w pierwszych kilku projektach, deweloperzy narzędzi tworzą szablon, który generuje, na podstawie modelu przepływu bagażu, większość kodu programu zmiennej i innych plików, takich jak dokumenty użytkownika. Znacznie skraca to czas opracowywania i poziom błędu dla każdego nowego projektu.

 Aby uzyskać więcej informacji, zobacz [Generowanie plików z modelu UML](../modeling/generate-files-from-a-uml-model.md).

## <a name="team-foundation-server-integration"></a>Integracja z serwerem Team Foundation
 Elementy robocze można łączyć z elementami modelu i programowo uzyskiwać dostęp do połączonych elementów.

 Deweloperzy narzędzia firmy Fabrikam piszą narzędzie, które generuje harmonogram pracy dla każdego projektu lotniska. Elementy robocze w harmonogramie są połączone z elementami modelu.

 Aby uzyskać więcej informacji, zobacz [Definiowanie programu obsługi łączy elementu pracy](../modeling/define-a-work-item-link-handler.md).

## <a name="tools-that-update-models"></a>Narzędzia aktualizujące modele
 Można tworzyć aplikacje autonomiczne i rozszerzenia programu Visual Studio, które mogą ładować modele UML.

 Deweloperzy firmy Fabrikam tworzą narzędzie, które odczytuje model i generuje raporty o postępie prac nad każdym elementem modelu.

 Aby uzyskać więcej informacji, zobacz [Odczyt modelu UML w kodzie programu](../modeling/read-a-uml-model-in-program-code.md).

## <a name="domain-specific-languages"></a>Języki specyficzne dla domeny
 Jeśli często używasz określonego typu modelu, może być przydatne do utworzenia języka specyficznego dla domeny. Można to zrobić, aby dopasować swoje potrzeby biznesowe bardziej niż model UML, ale wymaga więcej wysiłku, aby go zbudować i utrzymać go. Aby uzyskać więcej informacji, zobacz [Modelowanie SDK dla programu Visual Studio — Języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Linki**|
|------------------|---------------|
|**Filmy wideo**|![łącze do wideo](../data-tools/media/playvideo.gif "Wideo Play") [MSDN Jak mogę serii: Narzędzia UML i rozszerzalność](https://msdn.microsoft.com/vstudio/ff859492)<br /><br /> ![łącze do klipu wideo](../data-tools/media/playvideo.gif "Wideo Play") [Kanał 9: UML z programem Visual Studio](https://channel9.msdn.com/posts/clinted/)|
|**Fora**|-   [Narzędzia do modelowania & wizualizacji programu Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualization & Modelowanie SDK (NARZĘDZIA DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogi**|[Visual Studio ALM + Team Foundation Server Blog](https://blogs.msdn.com/b/visualstudioalm)|
|**Artykuły techniczne i czasopisma**|[Centrum architektury MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Zobacz też
 [Tworzenie modeli dla odwołania](../modeling/create-models-for-your-app.md) interfejsu API aplikacji [dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
