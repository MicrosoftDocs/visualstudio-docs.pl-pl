---
title: Tworzenie stron opcji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 368efaa78a56723d4a72c482bea9ee739385127e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709150"
---
# <a name="create-options-pages"></a>Tworzenie stron opcji
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ramach pakietu zarządzanego klas <xref:Microsoft.VisualStudio.Shell.DialogPage> pochodzących z rozszerzenia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE przez dodanie **opcji** stron w menu **Narzędzia.**

 Obiekt implementując dany **narzędzia Option** strona jest skojarzony z <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> określonych VSPackages przez obiekt.

 Ponieważ środowisko tworzenia wystąpienia obiektu implementując określonego **narzędzia opcje** strony, gdy dana strona jest wyświetlana przez IDE:

- Strona **Opcji narzędzi** powinna być zaimplementowana na własnym obiekcie, a nie na obiekcie implementującym vspackage.

- Obiekt nie może zaimplementować wielu stron **Opcji narzędzi.**

## <a name="register-as-a-tools-options-page-provider"></a>Zarejestruj się jako dostawca strony Opcje narzędzi
 VsPackage obsługi konfiguracji użytkownika za pośrednictwem **opcji narzędzia** strony wskazuje obiekty zapewniające te opcje <xref:Microsoft.VisualStudio.Shell.Package> **narzędzia** stron, stosując wystąpienia <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> zastosowane do implementacji.

 Musi istnieć jedno <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> wystąpienie dla każdego <xref:Microsoft.VisualStudio.Shell.DialogPage>typu pochodnego, który implementuje stronę Opcje **narzędzi.**

 Każde <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> wystąpienie używa typu, który implementuje stronę Opcje **narzędzi,** ciągów zawierających kategorię i podkategorię używaną do identyfikowania strony Opcje **narzędzi,** oraz informacji o zasobach w celu zarejestrowania typu jako strony opcje **narzędzi.**

## <a name="persist-tools-options-page-state"></a>Stan strony Opcje utrwalania narzędzi
 Jeśli implementacja strony **Opcje narzędzi** jest zarejestrowana z włączoną obsługą automatyzacji, IDE będzie się powtarzał stan strony wraz ze wszystkimi innymi stronami **Opcje narzędzi.**

 VsPackage można zarządzać własną trwałością <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>za pomocą . Należy zastosować tylko jedną lub inną metodę trwałości.

## <a name="implement-dialogpage-class"></a>Implementowanie klasy DialogPage
 Obiekt zapewniający implementację typu pochodnego <xref:Microsoft.VisualStudio.Shell.DialogPage>vsPackage może korzystać z następujących funkcji dziedziczonych:

- Domyślne okno interfejsu użytkownika.

- Domyślny mechanizm trwałości <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> dostępne, jeśli jest stosowany do <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> klasy lub `true` jeśli <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> właściwość jest ustawiona dla tego, który jest stosowany do klasy.

- Obsługa automatyzacji.

  Minimalnym wymaganiem dla obiektu implementującego <xref:Microsoft.VisualStudio.Shell.DialogPage> stronę Opcje **narzędzi** przy użyciu jest dodanie właściwości publicznych.

  Jeśli klasa poprawnie zarejestrowana jako dostawca strony **Opcje narzędzi,** jej właściwości publiczne są dostępne w sekcji **Opcje** menu **Narzędzia** w postaci siatki właściwości.

  Wszystkie te funkcje domyślne można zastąpić. Na przykład, aby utworzyć bardziej zaawansowany interfejs użytkownika wymaga tylko <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>zastąpienia domyślnej implementacji programu .

## <a name="example"></a>Przykład
 Poniżej znajduje się prosta implementacja strony opcji "Hello world". Dodanie następującego kodu do projektu domyślnego utworzonego przez szablon pakietu programu Visual Studio z wybraną opcją **Polecenie menu** odpowiednio zademonstruje funkcjonalność strony opcji.

### <a name="description"></a>Opis
 Następująca klasa definiuje minimalną stronę opcji "Hello world". Po otwarciu użytkownik może `HelloWorld` ustawić właściwość publiczną w siatce właściwości.

### <a name="code"></a>Code
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>Opis
 Zastosowanie następującego atrybutu do klasy pakietu udostępnia stronę opcji po załadowaniu pakietu. Liczby są dowolnymi identyfikatorami zasobów dla kategorii i strony, a wartość logiczna na końcu określa, czy strona obsługuje automatyzację.

### <a name="code"></a>Code
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>Opis
 Następujący program obsługi zdarzeń wyświetla wynik w zależności od wartości właściwości ustawionej na stronie opcji. Używa <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> metody z wynikiem jawnie rzutowane na typ strony opcji niestandardowej, aby uzyskać dostęp do właściwości udostępniane przez stronę.

 W przypadku projektu wygenerowanego przez szablon pakietu, wywołać tę funkcję z `MenuItemCallback` funkcji, aby dołączyć go do domyślnego polecenia dodanego do menu **Narzędzia.**

### <a name="code"></a>Code
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie ustawień i opcji użytkownika](../../extensibility/extending-user-settings-and-options.md)
- [Obsługa automatyzacji stron opcji](../../extensibility/internals/automation-support-for-options-pages.md)
