---
title: Weryfikowanie modelu UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8dfaf19e358d96b7737b06880d6fa4581b5c54f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659375"
---
# <a name="validate-your-uml-model"></a>Weryfikacja modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Niektóre modele UML, które można rysować w programie Visual Studio, mogą być uznawane za nieprawidłowe w projekcie. Na przykład może być konieczne, aby przypadek użycia był zawsze połączony z diagramem sekwencji, który ma linie życia reprezentujące aktorów przypadku użycia. Można zainstalować lub zdefiniować *ograniczenia* , które ułatwiają zespołowi spełnienie wymagań takich jak ten. Ograniczenia mogą być stosowane, gdy użytkownik zapisuje lub otwiera model i może być wywoływane przez polecenie menu.

 Żadne ograniczenia nie są dostarczane z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ponieważ zależą od tego, jak zespół interpretuje i używa modeli UML. Można jednak zdefiniować własne ograniczenia i zainstalować ograniczenia, które są zdefiniowane przez innych użytkowników. Aby dowiedzieć się, jak definiować ograniczenia i spakować je do dystrybucji, zobacz [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="invoking-validation"></a>Wywoływanie walidacji
 Jeśli zainstalowano rozszerzenie sprawdzania poprawności, zawarte w nim ograniczenia mogą być stosowane w następujących przypadkach. Niektóre ograniczenia są ustawione tak, aby dotyczyły tylko niektórych z tych przypadków.

- **Polecenie walidacji.** Aby wywoływać weryfikację w dowolnym momencie, kliknij przycisk **Weryfikuj model UML** w menu **Architektura** .

  > [!NOTE]
  > Polecenie pojawi się tylko wtedy, gdy są zainstalowane ograniczenia walidacji.

- **Przy zapisywaniu modelu.** Ograniczenia walidacji można zastosować podczas zapisywania modelu. Celem tych ograniczeń jest upewnienie się, że nie zapisano modelu, który jest nieprawidłowy w zależności od interpretacji projektu.

   Jeśli wystąpią błędy, zostanie wyświetlony monit z pytaniem, czy nadal chcesz zapisać model. Można wybrać, aby poprawić błędy lub zapisać model mimo to.

- **Przy otwieraniu modelu.** Po otwarciu modelu metody sprawdzania poprawności można zastosować do przywracania komunikatów o błędach, które istniały podczas zapisywania modelu. Błędy mogą być również wprowadzane przez niespójności między zmianami wprowadzonymi przez użytkowników, którzy pracują w różnych częściach modelu. Aby uzyskać więcej informacji, zobacz [udostępnianie modeli i eksportowanie diagramów](../modeling/share-models-and-exporting-diagrams.md).

  Błędy walidacji są raportowane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oknie błędy.

  Aby zaznaczyć w diagramie elementy, które są niepoprawne, kliknij dwukrotnie błąd. Działa to tylko wtedy, gdy nieprawidłowe elementy są widoczne na otwartym diagramie.

## <a name="installing-validation-constraints"></a>Instalowanie ograniczeń walidacji
 Ograniczenia są spakowane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] plikach rozszerzenia (VSIX). Zazwyczaj zestaw ograniczeń będzie częścią rozszerzenia, które również zawiera inne definicje, takie jak polecenia menu, profile i elementy przybornika.

#### <a name="to-install-a-visual-studio-extension"></a>Aby zainstalować rozszerzenie programu Visual Studio

1. Kliknij dwukrotnie plik **. vsix** w Eksploratorze Windows (lub Eksploratorze plików).

2. Uruchom ponownie dowolne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , które jest już uruchomione.

## <a name="disabling-and-uninstalling-validation-constraints"></a>Wyłączanie i odinstalowywanie ograniczeń walidacji
 Jeśli chcesz współpracować z modelem, do którego nie mają zastosowania ograniczenia, możesz tymczasowo wyłączyć rozszerzenie, które je zawiera. W ten sposób można współpracować z różnymi rodzajami modeli w różnym czasie, włączając i wyłączając różne rozszerzenia.

#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>Aby wyłączyć lub odinstalować rozszerzenie programu Visual Studio

1. W menu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Narzędzia** kliknij pozycję **Rozszerzenia i aktualizacje**.

2. Obok rozszerzenia kliknij pozycję **Wyłącz** , aby tymczasowo wyłączyć rozszerzenie. Można ją ponownie włączyć później, powracając do okna **rozszerzenia i aktualizacje** .

     \- oraz

     Kliknij przycisk **Odinstaluj** , aby usunąć rozszerzenie.

3. Uruchom ponownie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="see-also"></a>Zobacz też
 [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md) [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md) [Używanie modeli w procesie tworzenia](../modeling/use-models-in-your-development-process.md)
