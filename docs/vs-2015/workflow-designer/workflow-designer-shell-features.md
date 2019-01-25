---
title: Funkcje powłoki projektanta przepływu pracy | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6b432dd6dd0a19f6509ad1ff133424fcbc387fb6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790545"
---
# <a name="workflow-designer-shell-features"></a>Funkcje powłoki Projektanta przepływu pracy
[!INCLUDE[wfd1](../includes/wfd1-md.md)] składa się z trzech głównych obszarach interfejsu użytkownika: powierzchni projektanta i nad nim za pomocą paska nawigacji powłoki poniżej. Na pasku nawigacji, umieszczony w górnej części ekranu służy do wyświetlania listy elementów nadrzędnych bieżącego działania głównego. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Jak: Użyj do stron nadrzędnych](../workflow-designer/how-to-use-breadcrumb-navigation.md). Powierzchni projektanta umieszczony na środku ekranu jest używana do tworzenia przepływów pracy. Powłoka, umieszczony w dolnej części ekranu zawiera szereg przyciski umożliwiające zarządzanie bieżącym widokiem.  
  
## <a name="shell-features"></a>Funkcje powłoki  
 Powłoka zawiera przyciski po prawej stronie paska, który umożliwia powiększanie lub pomniejszanie przepływu pracy, do zawartości przepływu pracy do rozmiaru ekranu i Pokaż lub Ukryj mapowanie przeglądów. Użytkownik może również powiększyć lub pomniejszyć, przepływ pracy za pomocą skrótów klawiaturowych CTRL ++ i CTRL +-.  
  
## <a name="overview-map"></a>Mapowanie przeglądów  
 Mapowanie przeglądów wyświetla małą wersję działanie całej głównym bieżącego łączy do stron nadrzędnych, w tym wszystkie jego elementy podrzędne i wszystkie rozwinięte dzieci. Ma okienka ekranu, prostokąt z obramowaniem pomarańczowego, które przedstawia część działania aktualnie wyświetlany w edytorze. Przeciągnięcie prostokąt wokół mapowanie przeglądów Przewija projektanta przepływów pracy i zmiany widoku edytora.  
  
> [!NOTE]
>  [!INCLUDE[wfd2](../includes/wfd2-md.md)] Jest Zwirtualizowana interfejsu użytkownika. Projektanci działań są renderowane tylko wtedy, gdy jest to wymagane. Jeśli nigdy nie został wystawiony przez część przepływu pracy na powierzchni projektowej, część pojawia się jako białe na mapie Przegląd. Przewijanie wokół mapowanie przeglądów całkowicie rysuje przepływu pracy.  
  
## <a name="copying-or-saving-workflows-as-images"></a>Kopiowanie lub zapisywanie przepływów pracy jako obrazów  
 Przepływy pracy można skopiować format mapy bitowej lub zapisane w formacie mapy bitowej lub wektora. Kopiowanie lub zapisywanie obrazu umożliwia eksportowanie widoku całej aktywności głównym bieżącego łączy do stron nadrzędnych, w tym wszystkie jego elementy podrzędne i wszystkie rozwinięte dzieci do innego programu.  
  
 Aby skopiować jako obraz, kliknij prawym przyciskiem myszy projektanta i wybierz pozycję **Kopiuj jako obraz**. Aby zapisać jako obraz, kliknij prawym przyciskiem myszy projektanta i wybierz pozycję **Zapisz jako obraz**. Przepływy pracy można zapisać w formacie JPG, PNG, GIF lub XPS. Wybrano format **Zapisz jako** okno dialogowe w **Zapisz jako typ:** listy rozwijanej listy w dolnej części okna.  
  
## <a name="fonts-and-colors"></a>Czcionki i kolory  
 Czcionki używane w [!INCLUDE[wfd2](../includes/wfd2-md.md)] wewnątrz [!INCLUDE[vs2010](../includes/vs2010-md.md)] są kontrolowane przez czcionka środowiska. Kolory wyświetlane w [!INCLUDE[wfd2](../includes/wfd2-md.md)] zmiany, korzystając z dużego kontrastu schemat kolorów dla motywu systemu operacyjnego. Należy ponownie uruchomić [!INCLUDE[vs2010](../includes/vs2010-md.md)] po wprowadzeniu zmian w ustawieniach czcionek i kolorów, aby zmiany zostały wprowadzone [!INCLUDE[wfd2](../includes/wfd2-md.md)].