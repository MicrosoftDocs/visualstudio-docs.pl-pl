---
title: Tworzenie stronach opcji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d05b64f2245e4710f501ed8a24f7052cc310b30
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633086"
---
# <a name="create-options-pages"></a>Tworzenie stron opcji
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska pakietu zarządzanego klasy pochodne klasy <xref:Microsoft.VisualStudio.Shell.DialogPage> rozszerzyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, dodając **opcje** strony w obszarze **narzędzia** menu.

 Implementowanie obiektu danego **opcji narzędzia** strona jest skojarzona z określonych pakietów VSPackage przy <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> obiektu.

 Ponieważ środowisko tworzy obiekt implementujący określonego **opcje narzędzi** strony po wyświetleniu danej strony IDE:

-   A **opcji narzędzia** strony powinny zostać wdrożone na jego własnej obiektu, a nie na obiekt implementujący pakietu VSPackage.

-   Obiekt nie może implementować wiele **opcje narzędzi** stron.

## <a name="register-as-a-tools-options-page-provider"></a>Zarejestruj się jako dostawca strony opcji narzędzi
 Pakietu VSPackage pomocniczych konfiguracji użytkownika za pośrednictwem **opcje narzędzi** stron wskazuje obiektów zapewnia **opcje narzędzi** stron, stosując wystąpień <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> dotyczą <xref:Microsoft.VisualStudio.Shell.Package>implementacji.

 Musi mieć jedno wystąpienie <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> dla każdego <xref:Microsoft.VisualStudio.Shell.DialogPage>-pochodnych typu, który implementuje **opcje narzędzi** strony.

 Każde wystąpienie <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> używa typ, który implementuje **opcje narzędzi** stronie ciągów, które zawierają kategorii i podkategorii używany do identyfikowania **opcje narzędzi** strony i zasobów informacje, aby zarejestrować typ jako zapewniające **opcje narzędzi** strony.

## <a name="persist-tools-options-page-state"></a>Utrwalanie stanu strony opcji narzędzi
 Jeśli **opcje narzędzi** implementacja strony jest zarejestrowane w usłudze włączona obsługa automatyzacji, IDE utrzymuje stanu strony oraz wszystkich innych **opcje narzędzi** stron.

 Pakietu VSPackage można zarządzać własną trwałości za pomocą <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Należy używać tylko jednego lub inna metoda trwałości.

## <a name="implement-dialogpage-class"></a>Implementowanie klasy elementu DialogPage
 Obiekt dostarczający wdrożenia pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.DialogPage>-typu pochodnego korzystać z zalet dziedziczone następujące funkcje:

- Domyślne okno interfejsu użytkownika.

- Element domyślny dostępnego mechanizmu stanu trwałego albo jeśli <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> jest stosowany do klasy, lub jeśli <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> właściwość jest ustawiona na `true` dla <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> mający zastosowanie do klasy.

- Obsługa automatyzacji.

  Minimalne wymagania dotyczące implementowania obiektu **opcje narzędzi** strony <xref:Microsoft.VisualStudio.Shell.DialogPage> jest dodanie właściwości publiczne.

  Jeśli klasa jest prawidłowo zarejestrowana jako **opcje narzędzi** strony dostawcy, a następnie jego właściwości publiczne są dostępne na **opcje** części **narzędzia** menu w formie siatki właściwości.

  Wszystkie te funkcje domyślne można przesłonić. Na przykład można utworzyć bardziej zaawansowane użytkownika interfejsu wymaga tylko zastępowanie domyślna Implementacja klasy <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.

## <a name="example"></a>Przykład
 Poniżej jest implementacją proste "Hello world" na stronie opcji. Dodając następujący kod do projektu domyślne utworzone przez szablon pakietu Visual Studio za pomocą **polecenia Menu** wybrana opcja odpowiednio zademonstruje funkcji strony opcji.

### <a name="description"></a>Opis
 Następujące klasy definiuje Strona opcji minimalnej "Hello world". Po otwarciu, użytkownik może ustawić publicznie `HelloWorld` właściwości w siatce właściwości.

### <a name="code"></a>Kod
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>Opis
 Stosowanie następujących atrybutów do klasy pakietu udostępnia opcje strony podczas ładowania pakietu. Liczby są dowolne identyfikatory zasobów dla kategorii i strony, a wartość logiczną na końcu Określa, czy strona obsługuje usługi automation.

### <a name="code"></a>Kod
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>Opis
 Następujący program obsługi zdarzeń wyświetla wynik w zależności od wartości właściwości strony opcje. Używa ona <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> metody z wynikiem jawnie rzutowane na typ strony opcja niestandardowa uzyskiwania dostępu do właściwości udostępniane przez stronę.

 W przypadku projektu generowane przez szablon pakietu, należy wywołać tę funkcję z `MenuItemCallback` funkcję, aby dołączyć go do domyślnego polecenia dodane do **narzędzia** menu.

### <a name="code"></a>Kod
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>Zobacz także
- [Rozszerzenie Opcje i ustawienia użytkownika](../../extensibility/extending-user-settings-and-options.md)
- [Automatyzacja obsługi dla stron opcji](../../extensibility/internals/automation-support-for-options-pages.md)