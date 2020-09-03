---
title: Tworzenie stron opcji | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196949"
---
# <a name="creating-options-pages"></a>Tworzenie stron opcji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] strukturze pakietów zarządzanych klasy pochodzące od <xref:Microsoft.VisualStudio.Shell.DialogPage> rozszerzeń [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE przez dodanie stron **opcji** w menu **Narzędzia** .  
  
 Obiekt implementujący daną stronę **opcji narzędzi** jest skojarzony z konkretną pakietów VSPackage przez <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> obiekt.  
  
 Ze względu na to, że środowisko tworzy wystąpienie obiektu implementującego konkretne strony **opcji narzędzi** , gdy dana strona jest wyświetlana przez IDE:  
  
- Strona **opcji narzędzia** powinna zostać zaimplementowana na swoim obiekcie, a nie na obiekcie implementującym pakietu VSPackage.  
  
- Obiekt nie może zaimplementować wielu stron **opcji narzędzi** .  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Rejestrowanie jako dostawca strony opcji narzędzi  
 Pakietu VSPackage Obsługa konfiguracji użytkownika za pomocą stron **Opcje narzędzi** wskazuje obiekty udostępniające te strony **opcji narzędzi** , stosując wystąpienia <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> zastosowane do <xref:Microsoft.VisualStudio.Shell.Package> implementacji.  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>Dla każdego <xref:Microsoft.VisualStudio.Shell.DialogPage> typu pochodnego, który implementuje stronę **opcji narzędzi** , musi istnieć jedno wystąpienie.  
  
 Każde wystąpienie programu <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> używa typu, który implementuje stronę **Opcje narzędzi** , ciągi, które zawierają kategorię i podkategorię służącą do identyfikowania strony **Opcje narzędzi** i informacje o zasobach w celu zarejestrowania typu jako strony **opcji narzędzi** .  
  
## <a name="persisting-tools-options-page-state"></a>Utrwalanie opcji narzędzi — stan strony  
 Jeśli implementacja strony **opcji narzędzi** jest zarejestrowana z włączoną obsługą automatyzacji, środowisko IDE utrzymuje stan strony wraz ze wszystkimi innymi stronami **opcji narzędzi** .  
  
 Pakietu VSPackage może zarządzać własną trwałość przy użyciu <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . Należy używać tylko jednej lub innej metody trwałości.  
  
## <a name="implementing-dialogpage-class"></a>Implementowanie klasy typu DialogPage  
 Obiekt zapewniający implementację <xref:Microsoft.VisualStudio.Shell.DialogPage> typu pochodnego przez pakietu VSPackage może korzystać z następujących dziedziczonych funkcji:  
  
- Domyślne okno interfejsu użytkownika.  
  
- Domyślny mechanizm trwałości dostępny w przypadku <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> zastosowania go do klasy lub jeśli <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> Właściwość jest ustawiona na `true` dla elementu <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> , który jest stosowany do klasy.  
  
- Obsługa automatyzacji.  
  
  Minimalnym wymaganiem dla obiektu implementującego stronę **opcji narzędzi** przy użyciu <xref:Microsoft.VisualStudio.Shell.DialogPage> jest dodanie właściwości publicznych.  
  
  Jeśli klasa została prawidłowo zarejestrowana jako dostawca strony **opcji narzędzia** , a następnie właściwości publiczne są dostępne w sekcji **Opcje** menu **Narzędzia** w postaci siatki właściwości.  
  
  Wszystkie te funkcje domyślne mogą zostać zastąpione. Na przykład, aby utworzyć bardziej zaawansowany interfejs użytkownika, wymaga przesłania tylko domyślnej implementacji <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> .  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się prosta implementacja "Hello World" strony opcji. Dodanie następującego kodu do domyślnego projektu utworzonego przez szablon pakietu programu Visual Studio z wybraną opcją **polecenia menu** spowoduje odpowiednie zademonstrowanie funkcji strony opcji.  
  
### <a name="description"></a>Opis  
 Poniższa klasa definiuje minimalną stronę opcji "Hello World". Po otwarciu użytkownik może ustawić właściwość publiczną `HelloWorld` w siatce właściwości.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs#11)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb#11)]  
  
### <a name="description"></a>Opis  
 Zastosowanie następującego atrybutu do klasy Package powoduje, że strona opcji jest dostępna po załadowaniu pakietu. Liczby są dowolnymi identyfikatorami zasobów dla kategorii i strony, a wartość logiczna na końcu określa, czy strona obsługuje automatyzację.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#07)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#07)]  
  
### <a name="description"></a>Opis  
 Poniższy program obsługi zdarzeń wyświetla wynik w zależności od wartości właściwości ustawionej na stronie Opcje. Używa <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> metody z wynikiem jawnie rzutowania na typ strony opcji niestandardowej, aby uzyskać dostęp do właściwości uwidocznionych na stronie.  
  
 W przypadku projektu wygenerowanego przez szablon pakietu Wywołaj tę funkcję z `MenuItemCallback` funkcji, aby dołączyć ją do domyślnego polecenia dodawanego do menu **Narzędzia** .  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#08)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#08)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie ustawień i opcji użytkownika](../../extensibility/extending-user-settings-and-options.md)   
 [Obsługa automatyzacji dla stron opcji](../../extensibility/internals/automation-support-for-options-pages.md)
