---
title: Strona usług, Projektant projektu
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 406e8fbb16d3cac4b755b0532f3916fed486e466
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919000"
---
# <a name="services-page-project-designer"></a>Strona usług, Projektant projektu

Usługi aplikacji klienta zapewniają uproszczony dostęp [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] do danych logowania, ról i usług profilów z aplikacji Windows Forms i Windows Presentation Foundation (WPF). Możesz użyć strony **usługi** **projektanta projektu** , aby włączyć i skonfigurować usługi aplikacji klienta dla projektu.

Za pomocą usług aplikacji klienckich można używać scentralizowanego serwera do uwierzytelniania użytkowników, określania przypisanej roli lub ról poszczególnych użytkowników oraz przechowywania ustawień aplikacji dla poszczególnych użytkowników, które można udostępniać w sieci. Aby uzyskać więcej informacji, zobacz [usługi aplikacji klienta](/dotnet/framework/common-client-technologies/client-application-services).

Aby uzyskać dostęp do strony **usługi** , wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie kliknij pozycję **Właściwości** w menu **projekt** . Gdy zostanie wyświetlony **Projektant projektu** , kliknij kartę **usługi** .

## <a name="task-list"></a>Lista zadań

[Instrukcje: Konfigurowanie Usługi aplikacji klienta](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Lista elementów UI

 **Konfiguracja**

Ta kontrolka nie jest edytowalna na tej stronie. Aby uzyskać opis tego formantu, zobacz [stronę Kompilacja, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) lub [stronę kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platformach**

Ta kontrolka nie jest edytowalna na tej stronie. Aby uzyskać opis tego formantu, zobacz [stronę Kompilacja, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) lub [stronę kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Włącz usługi aplikacji klienta**

Wybierz, aby włączyć usługi aplikacji klienta. Aby korzystać z usług aplikacji klienta, należy określić lokalizacje usług na stronie **usługi** .

 **Użyj uwierzytelniania systemu Windows**

Wskazuje, że dostawca uwierzytelniania będzie używał uwierzytelniania opartego na systemie Windows, czyli tożsamości dostarczonej przez system operacyjny Windows.

 **Użyj uwierzytelniania formularzy**

Wskazuje, że dostawca uwierzytelniania będzie korzystał z uwierzytelniania formularzy. Oznacza to, że aplikacja musi zapewnić interfejs użytkownika do logowania. Aby uzyskać więcej informacji, zobacz [jak: Zaimplementuj Logowanie użytkownika przy użyciu](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services)usługi aplikacji klienta.

 **Lokalizacja usługi uwierzytelniania**

Używany tylko z uwierzytelnianiem formularzy. Określa lokalizację usługi uwierzytelniania.

 **Obowiązkowe Dostawca poświadczeń**

Używany tylko z uwierzytelnianiem formularzy. Wskazuje implementację, która będzie używana przez usługę uwierzytelniania do wyświetlania okna dialogowego logowania, gdy aplikacja `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> wywołuje metodę i przekazuje puste ciągi lub `null` parametry. <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> Jeśli to pole pozostanie puste, należy przekazać do <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> metody prawidłową nazwę użytkownika i hasło. Należy określić dostawcę poświadczeń jako nazwę typu kwalifikowanego dla zestawu. Aby uzyskać więcej informacji, <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> Zobacz i [nazwy zestawów](/dotnet/framework/app-domains/assembly-names). W najprostszej postaci nazwa typu kwalifikowana dla zestawu wygląda podobnie do poniższego przykładu:`MyNamespace.MyLoginClass, MyAssembly`

 **Lokalizacja usługi ról**

Określa lokalizację usługi ról.

 **Lokalizacja usługi ustawień sieci Web**

Określa lokalizację usługi profilu (Ustawienia sieci Web).

 **Zaawansowane**

Otwiera okno [dialogowe Ustawienia zaawansowane dla usług](../../ide/reference/advanced-settings-for-services-dialog-box.md), za pomocą którego można przesłonić zachowanie domyślne. Na przykład można użyć tego okna dialogowego, aby określić bazę danych do przechowywania w trybie offline, zamiast korzystać z lokalnego systemu plików. Aby uzyskać więcej informacji, zobacz [okno dialogowe Ustawienia zaawansowane dla usług](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Zobacz także

- [Usługi aplikacji klienckich](/dotnet/framework/common-client-technologies/client-application-services)
- [Zaawansowane ustawienia dla usług, okno dialogowe](../../ide/reference/advanced-settings-for-services-dialog-box.md)
- [Instrukcje: Konfigurowanie Usługi aplikacji klienta](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
- [Strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)
