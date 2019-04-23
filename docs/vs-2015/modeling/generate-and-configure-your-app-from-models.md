---
title: Generowanie i konfigurowanie aplikacji na podstawie modeli | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 4dc8f572-a09e-4d19-a92d-f1df383e728b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bb12d80c581b0ea0b605932083cf4f62fe764e30
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073491"
---
# <a name="generate-and-configure-your-app-from-models"></a>Generowanie i konfigurowanie aplikacji na podstawie modeli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można wygenerować lub skonfigurować poszczególnych części aplikacji z modelu. Model może mieć UML lub języka DSL.  
  
 Model reprezentuje wymagania bezpośrednio niż kod. Wynikające zachowanie aplikacji bezpośrednio z modelu, można odpowiedzieć zmienionych wymagań znacznie szybciej i niezawodny niż przez aktualizowania kodu. Mimo że niektóre roboczego jest wymagane do skonfigurowania tworzenia elementów pochodnych, inwestycji jest zwracany, jeśli oczekujesz, zmiany w wymaganiach lub jeśli planujesz wprowadzić kilka wariantów produktu.  
  
## <a name="generating-the-code-of-your-application-from-a-model"></a>Generowanie kodu aplikacji na podstawie modelu  
 Najprostszym sposobem, aby wygenerować kod jest przy użyciu szablonów tekstowych. Istnieje możliwość wygenerowania kodu, w tym samym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania, w którym są przechowywane modelu. Aby uzyskać więcej informacji, zobacz:  
  
- [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
- [Generowanie plików na podstawie modelu UML](../modeling/generate-files-from-a-uml-model.md)  
  
- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)  
  
  Ta metoda jest łatwy do zastosowania przyrostowo. Uruchom z aplikacją, która działa tylko dla określonych przypadków i wybierz kilka części, którą chcesz się nieznacznie różnić od modelu. Zmień nazwę plików źródłowych z tych elementów, dzięki czemu staną się tekst, pliki szablonów (.tt). W tym momencie .cs pliki źródłowe zostaną automatycznie wygenerowane z plików szablonów, dzięki czemu aplikacja będzie działać tak jak poprzednio.  
  
  Następnie możesz wykonać jedną z części pakietu kodu i Zamień wyrażenia szablonu tekstu, który odczytuje model i generuje część pliku źródłowego. Co najmniej jedną wartość modelu będzie generował oryginalne źródło, aby ponownie uruchomić aplikację i będzie ona działać tak jak poprzednio. Po przetestowaniu modelu różnych wartości, możesz przejść do wstawienia wyrażeń szablonu w innej części kodu.  
  
  Ta metoda przyrostowe oznacza, że generowanie kodu zwykle podejścia o niskim ryzyku. Wynikowy aplikacje zwykle wykonać prawie oraz odręcznej wersji.  
  
  Jednak w przypadku uruchomienia z istniejącą aplikacją, może się okazać, że wiele refaktoryzacji jest wymagany do oddzielania różne zachowania, które są zarządzane przez model, dzięki czemu mogą być niezależne zróżnicowane. Firma Microsoft zaleca oceny ten aspekt aplikacji, podczas szacowania kosztów projektu.  
  
## <a name="configuring-your-application-from-a-model"></a>Konfigurowanie własnej aplikacji z modelu  
 Jeśli chcesz zróżnicować zachowanie aplikacji w czasie wykonywania, nie można użyć generowania kodu, który generuje kod źródłowy, zanim aplikacja jest kompilowana. Zamiast tego można zaprojektować aplikację odczytywanie modelu UML lub DSL i różnią się odpowiednio jego zachowanie. Aby uzyskać więcej informacji, zobacz:  
  
- [Odczytywanie modelu UML w kodzie programu](../modeling/read-a-uml-model-in-program-code.md)  
  
- [Instrukcje: Otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
  Ta metoda również będą stosowane przyrostowo, ale ma więcej pracy na początku. Musisz napisać kod, który będzie odczytania modelu i skonfigurować strukturę, która zezwala na jego wartości umożliwić dostęp do zmiennej części. Zmienna części ogólnego jest droższe niż generowania kodu.  
  
  Aplikacja ogólna zwykle wykonuje mniej również niż ich odpowiedniki określone. Jeśli wydajność ma kluczowe znaczenie podczas, plan projektu powinna zawierać oceny tego ryzyka.  
  
## <a name="developing-a-derived-application"></a>Opracowywanie aplikacji pochodne  
 Ogólne wytyczne mogą się okazać przydatne.  
  
- **Uruchom określone, a następnie Uogólnij.** Najpierw zapisać określoną wersję aplikacji. Ta wersja powinny działać w jeden zestaw warunków. Jeżeli jesteś zadowolony jej działa poprawnie, możesz wprowadzić niektóre pochodzi z modelu. Rozszerz stopniowo pochodnej części.  
  
     Na przykład projekt witryny sieci Web, która ma określony zestaw stron sieci Web, przed rozpoczęciem projektowania aplikacji sieci Web, która przedstawia stron, które są zdefiniowane w modelu.  
  
- **Model wariantu aspektów.** Zidentyfikuj aspektów, które będą się różnić między wdrażania jednego i drugiego, lub wraz z upływem czasu zgodnie z wymaganiami zmienić. Są to aspektów, które powinny pochodzić z modelu.  
  
     Na przykład jeśli zestaw Web pages i łączy między ich zmiany, ale styl i format stron jest zawsze taki sam, a następnie modelu powinna opisywać łącza, ale nie ma do opisywania formatu stron.  
  
- **Oddzielne uwagi.** Jeśli zmiennej aspekty można podzielić na niezależne obszarów, należy użyć oddzielnych modeli dla każdego obszaru. ModelBus można zdefiniować operacje, które mają wpływ na modelach i ograniczenia między nimi.  
  
     Na przykład można użyć jednego modelu do zdefiniowania Nawigacja między stronami sieci Web i innego modelu, do definiowania układu strony. Aby uzyskać więcej informacji, zobacz [modeli UML, integracja z innymi modelami i narzędziami](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
- **Model wymóg nie rozwiązania.** Zaprojektuj język DSL lub dostosować UML, tak, aby go w tym artykule opisano wymagania użytkownika. Z drugiej strony nie należy projektować notacji zgodnie ze zmiennej aspektów implementacji.  
  
     Na przykład model nawigacyjnych w sieci Web powinny reprezentować stron sieci Web i hiperłączy między nimi. Model nawigacyjnych w sieci Web nie powinny reprezentować fragmenty kodu HTML lub klas w aplikacji.  
  
- **Generowanie i interpretowania?** Jeśli wymagania dotyczące określonego wdrożenia będą rzadko się zmieniają, generowania kodu programu z modelu. Jeśli wymagania często mogą ulec zmianie lub mogą współistnieć w więcej niż jeden typ variant, w tym samym wdrożeniu, wówczas aplikacja jest zapisywana tak, aby można odczytać i zinterpretować modelu.  
  
     Na przykład jeśli używasz modelu witryny sieci Web do tworzenia szereg różnych i oddzielnie zainstalowanego witryn sieci Web, następnie należy generować kod witryny z modelu. Jednak go użyć modelu do sterowania lokacji, która zmienia się codziennie, a następnie jest napisanie serwera sieci Web, który odczytuje model i przedstawia informacje o lokacji.  
  
- **UML lub DSL?** Należy rozważyć utworzenie usługi notacji modelowania przy użyciu stereotypy w celu rozszerzenia UML. Jeśli nie diagramu UML, która pasuje do tego celu, należy zdefiniować języka DSL. Jednak należy unikać istotne semantyce UML.  
  
     Na przykład diagram klas UML jest Kolekcja pól i strzałki; w tym notacji może teoretycznie zdefiniujesz niczego. Jednak nie zaleca się użycie na diagramie klasy, z wyjątkiem sytuacji, gdy są w rzeczywistości opisujące zestaw typów. Na przykład można przystosować diagramów klas do opisania różnych typów stron sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie plików z modelu UML](../modeling/generate-files-from-a-uml-model.md)   
 [Odczytywanie modelu UML w kodzie programu](../modeling/read-a-uml-model-in-program-code.md)   
 [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)   
 [Instrukcje: Otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
