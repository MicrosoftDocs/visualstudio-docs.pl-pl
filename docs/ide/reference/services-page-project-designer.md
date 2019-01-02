---
title: Strona usług, Projektant projektu
ms.date: 01/18/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c3e40108f6bca3226e6f39eb2eb4b09437a4f1e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952384"
---
# <a name="services-page-project-designer"></a>Strona usług, Projektant projektu

Usługi aplikacji klienta zapewniają uproszczony dostęp do [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] logowania, ról i usług profilu z aplikacji Windows Forms i Windows Presentation Foundation (WPF). Możesz użyć **usług** strony **projektanta projektu** Włączanie i konfigurowanie usług aplikacji klienckich dla Twojego projektu.

Przy użyciu usług aplikacji klienta centralny serwer służy do uwierzytelniania użytkowników, określić każdy użytkownik przypisaną rolę lub role i przechowywać ustawienia aplikacji na użytkownika, które można udostępniać w sieci. Aby uzyskać więcej informacji, zobacz [usług aplikacji klienta](/dotnet/framework/common-client-technologies/client-application-services).

Aby uzyskać dostęp do **usług** wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie kliknij przycisk **właściwości** na **projektu** menu. Podczas **projektanta projektu** zostanie wyświetlona, kliknij przycisk **usług** kartę.

## <a name="task-list"></a>Lista zadań

[Instrukcje: Konfigurowanie usług aplikacji klienta](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Lista elementów UI

 **Konfiguracja**

 Ta kontrolka nie jest edytowalny na tej stronie. Aby uzyskać opis tego formantu, zobacz [strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) lub [Stroka kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platforma**

 Ta kontrolka nie jest edytowalny na tej stronie. Aby uzyskać opis tego formantu, zobacz [strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) lub [Stroka kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Włączyć usługi aplikacji klienckiej**

 Zaznacz, aby włączyć usługi aplikacji klienckiej. Należy określić lokalizacje usługi na **usług** strony do użycia usług aplikacji klienta.

 **Uwierzytelnianie Windows**

 Wskazuje, że dostawca uwierzytelniania będzie używać uwierzytelniania opartego na Windows, czyli tożsamości dostarczonych przez system operacyjny Windows.

 **Korzystanie z uwierzytelniania formularzy**

 Wskazuje, że dostawca uwierzytelniania będzie używać uwierzytelniania formularzy. Oznacza to, że aplikacji należy podać interfejsu użytkownika dla nazwy logowania. Aby uzyskać więcej informacji, zobacz [jak: Implementowanie logowania użytkownika przy użyciu usług aplikacji klienta](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).

 **Lokalizacja usługi uwierzytelniania**

 Używany tylko z uwierzytelniania formularzy. Określa lokalizację usługi uwierzytelniania.

 **Opcjonalnie: Dostawca poświadczeń**

 Używany tylko z uwierzytelniania formularzy. Wskazuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> implementacji, które będzie używane przez usługę uwierzytelniania, aby wyświetlić okno dialogowe logowania, gdy Twoja aplikacja wywołuje `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> metody i przekazuje puste ciągi lub `null` dla parametrów. Jeśli to pole pozostanie puste, należy podać prawidłową nazwę użytkownika i hasło, aby <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> metody. Dostawca poświadczeń należy określić nazwę typu kwalifikowanego zestawu. Aby uzyskać więcej informacji, zobacz <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> i [nazw zestawów](/dotnet/framework/app-domains/assembly-names). W najprostszej postaci nazwę typu kwalifikowanego zestawu wyglądają podobnie do poniższego przykładu: `MyNamespace.MyLoginClass, MyAssembly`

 **Lokalizacja usługi ról**

 Określa lokalizację usługi ról.

 **Ustawienia sieci Web usługi lokalizacji**

 Określa lokalizację profilu usługi (ustawienia internetowe).

 **Zaawansowane**

 Otwiera [Zaawansowane ustawienia dla usług, okno dialogowe](../../ide/reference/advanced-settings-for-services-dialog-box.md), którego można użyć, aby zastąpić domyślne zachowanie. Na przykład służy to okno dialogowe, aby określić bazę danych magazynu offline, zamiast korzystać z lokalnego systemu plików. Aby uzyskać więcej informacji, zobacz [Zaawansowane ustawienia dla usług, okno dialogowe](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Zobacz także

- [Usługi aplikacji klienckich](/dotnet/framework/common-client-technologies/client-application-services)
- [Zaawansowane ustawienia dla usług, okno dialogowe](../../ide/reference/advanced-settings-for-services-dialog-box.md)
- [Instrukcje: Konfigurowanie usług aplikacji klienta](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
- [Strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)
