---
title: Tworzenie stronach opcji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c2b993a6c6947adfa3b01f2947b992b23236b8f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196949"
---
# <a name="creating-options-pages"></a>Tworzenie stron opcji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowiska pakietu zarządzanego klasy pochodne klasy <xref:Microsoft.VisualStudio.Shell.DialogPage> rozszerzyć [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE, dodając **opcje** strony w obszarze **narzędzia** menu.  
  
 Implementowanie obiektu danego **opcji narzędzia** strona jest skojarzona z określonych pakietów VSPackage przy <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> obiektu.  
  
 Ponieważ środowisko tworzy obiekt implementujący określonego **opcje narzędzi** strony po wyświetleniu danej strony IDE:  
  
- A **opcji narzędzia** strony powinny zostać wdrożone na jego własnej obiektu, a nie na obiekt implementujący pakietu VSPackage.  
  
- Obiekt nie może implementować wiele **opcje narzędzi** stron.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Rejestrowanie dostawcy strony opcji narzędzi  
 Pakietu VSPackage pomocniczych konfiguracji użytkownika za pośrednictwem **opcje narzędzi** stron wskazuje obiektów zapewnia **opcje narzędzi** stron, stosując wystąpień <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> dotyczą <xref:Microsoft.VisualStudio.Shell.Package>implementacji.  
  
 Musi mieć jedno wystąpienie <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> dla każdego <xref:Microsoft.VisualStudio.Shell.DialogPage>-pochodnych typu, który implementuje **opcje narzędzi** strony.  
  
 Każde wystąpienie <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> używa typ, który implementuje **opcje narzędzi** stronie ciągów, które zawierają kategorii i podkategorii używany do identyfikowania **opcje narzędzi** strony i zasobów informacje, aby zarejestrować typ jako zapewniające **opcje narzędzi** strony.  
  
## <a name="persisting-tools-options-page-state"></a>Utrwalanie stanu strony opcji narzędzi  
 Jeśli **opcje narzędzi** implementacja strony jest zarejestrowane w usłudze włączona obsługa automatyzacji, IDE utrzymuje stanu strony oraz wszystkich innych **opcje narzędzi** stron.  
  
 Pakietu VSPackage można zarządzać własną trwałości za pomocą <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Należy używać tylko jednego lub inna metoda trwałości.  
  
## <a name="implementing-dialogpage-class"></a>Implementacja klasy elementu DialogPage  
 Obiekt dostarczający wdrożenia pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.DialogPage>-typu pochodnego korzystać z zalet dziedziczone następujące funkcje:  
  
- Domyślne okno interfejsu użytkownika.  
  
- Element domyślny dostępnego mechanizmu stanu trwałego albo jeśli <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> jest stosowany do klasy, lub jeśli <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> właściwość jest ustawiona na `true` dla <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> mający zastosowanie do klasy.  
  
- Obsługa automatyzacji.  
  
  Minimalne wymagania dotyczące implementowania obiektu **opcje narzędzi** strony <xref:Microsoft.VisualStudio.Shell.DialogPage> jest dodanie właściwości publiczne.  
  
  Jeśli klasa jest prawidłowo zarejestrowana jako **opcje narzędzi** strony dostawcy, a następnie jego właściwości publiczne są dostępne na **opcje** części **narzędzia** menu w formie siatki właściwości.  
  
  Wszystkie te funkcje domyślne można przesłonić. Na przykład można utworzyć bardziej zaawansowane użytkownika interfejsu wymaga tylko zastępowanie domyślna Implementacja klasy <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Przykład  
 Poniżej jest proste wdrażanie "hello world" na stronie opcji. Dodając następujący kod do projektu domyślne utworzona przez szablon do pakietu Visual Studio, za pomocą **polecenia Menu** wybrana opcja odpowiednio zademonstruje funkcji strony opcji.  
  
### <a name="description"></a>Opis  
 Następujące klasy definiuje minimalna strona Opcje "hello world". Po otwarciu, użytkownik może ustawić publicznie `HelloWorld` właściwości w siatce właściwości.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs#11)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb#11)]  
  
### <a name="description"></a>Opis  
 Stosowanie następujących atrybutów do klasy pakietu udostępnia opcje strony podczas ładowania pakietu. Liczby są dowolne identyfikatory zasobów dla kategorii i strony, a wartość logiczną na końcu Określa, czy strona obsługuje usługi automation.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#07)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#07)]  
  
### <a name="description"></a>Opis  
 Następujący program obsługi zdarzeń wyświetla wynik w zależności od wartości właściwości strony opcje. Używa ona <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> metody z wynikiem jawnie rzutowane na typ strony opcja niestandardowa uzyskiwania dostępu do właściwości udostępniane przez stronę.  
  
 W przypadku projektu generowane przez szablon pakietu, należy wywołać tę funkcję z `MenuItemCallback` funkcję, aby dołączyć go do domyślnego polecenia dodane do **narzędzia** menu.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#08)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#08)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie ustawień użytkownika ani opcji](../../extensibility/extending-user-settings-and-options.md)   
 [Obsługa automatyzacji dla stron opcji](../../extensibility/internals/automation-support-for-options-pages.md)
