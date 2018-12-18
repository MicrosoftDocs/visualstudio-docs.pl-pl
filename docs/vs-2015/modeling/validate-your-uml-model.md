---
title: Weryfikacja modelu UML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fea958a20e5eee78f79f324ad19ef646f7920951
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739969"
---
# <a name="validate-your-uml-model"></a>Weryfikacja modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Niektóre modele UML, które można narysować w programie Visual Studio może zostać uznane za nieprawidłowe w projekcie. Na przykład wymagać, że przypadek użycia musi być zawsze połączone z diagramu sekwencji, która ma linie życia reprezentujące aktorów przypadek użycia. Można zainstalować lub zdefiniować *ograniczenia* , Pomóż swojemu zespołowi, aby były zgodne z wymaganiami, takie jak to. Ograniczenia mogą być stosowane, gdy użytkownik zapisuje lub otwiera modelu i może być wywoływany przez polecenie menu.  
  
 Bez ograniczeń są dostarczane z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ponieważ są one zależne od jak zespół interpretuje i używa w modelach UML. Jednak możesz zdefiniować własne ograniczenia i zainstalować ograniczenia, które są zdefiniowane przez innych użytkowników. Aby dowiedzieć się, jak zdefiniować ograniczenia i spakować je do dystrybucji, zobacz [definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
## <a name="invoking-validation"></a>Wywoływanie walidacji  
 Po zainstalowaniu rozszerzenia sprawdzania poprawności ograniczenia, które zapewnia mogą być stosowane w następujących przypadkach. Niektóre ograniczenia są ustawione do zastosowania w tylko niektóre z tych przypadków.  
  
- **Polecenie sprawdzania poprawności.** Aby wywołać sprawdzania poprawności w dowolnym momencie, kliknij przycisk **Sprawdź poprawność modelu UML** na **architektury** menu.  
  
  > [!NOTE]
  >  Polecenie będą wyświetlane tylko wtedy, gdy ograniczenia sprawdzania poprawności są zainstalowane.  
  
- **Przy zapisywaniu modelu.** Po zapisaniu modelu można zastosować ograniczenia sprawdzania poprawności. Te ograniczenia ma na celu pomóc, upewnij się, nie należy zapisywać modelu, który jest nieprawidłowa przy uwzględnieniu interpretacji projektu.  
  
   Jeśli wystąpią błędy, zostanie wyświetlony pytaniem, czy nadal chcesz zapisać model. Możesz poprawić błędy lub zapisać mimo to model.  
  
- **Otwieranie modelu.** Podczas otwierania modelu metody sprawdzania poprawności można zastosować do przywrócenia komunikaty o błędach, które istniały podczas zapisywania modelu. Błędy mogą być także wprowadzone przez niespójności między zmiany wprowadzone przez użytkowników, którzy pracują na różnych częściach modelu. Aby uzyskać więcej informacji, zobacz [udostępnianie modeli i eksportowanie diagramów](../modeling/share-models-and-exporting-diagrams.md).  
  
  Błędy sprawdzania poprawności są zgłaszane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oknie błędów.  
  
  Aby wybrać na diagramie elementy, które są nieprawidłowe, klikaj dwukrotnie poszczególne błędy. Ta funkcja działa tylko w przypadku, gdy niepoprawne elementy są widoczne w Otwórz diagram.  
  
## <a name="installing-validation-constraints"></a>Instalowanie ograniczeń walidacji  
 Ograniczenia są pakowane w ramach [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pliki rozszerzenia (VSIX). Zazwyczaj zestawem ograniczeń jest częścią rozszerzenia, które zawiera również inne definicje, takich jak polecenia menu, profile i elementy do przybornika.  
  
#### <a name="to-install-a-visual-studio-extension"></a>Aby zainstalować rozszerzenia programu Visual Studio  
  
1.  Kliknij dwukrotnie **.vsix** pliku w Eksploratorze Windows (lub Eksploratora plików).  
  
2.  Ponownie uruchom dowolne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , jest już uruchomiony.  
  
## <a name="disabling-and-uninstalling-validation-constraints"></a>Wyłączanie i odinstalowywania ograniczenia sprawdzania poprawności  
 W przypadku pracy z modelem, do którego nie stosuje ograniczenia może tymczasowo wyłączyć rozszerzenie, które je zawiera. W ten sposób pozwala pracować z różnymi rodzajami modeli w różnym czasie, włączania i wyłączania rozszerzeń.  
  
#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>Aby wyłączyć lub odinstalować rozszerzenia programu Visual Studio  
  
1.  Na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.  
  
2.  Obok rozszerzenia, kliknij przycisk **wyłączyć** tymczasowo wyłączyć rozszerzenie. Możesz ją włączyć ponownie później, wracając do **rozszerzenia i aktualizacje** okna.  
  
     \- lub —  
  
     Kliknij przycisk **Odinstaluj** można usunąć rozszerzenia.  
  
3.  Uruchom ponownie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)   
 [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)



