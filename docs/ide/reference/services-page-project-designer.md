---
title: Strona usług, Projektant projektu
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d30d8e8ddcdc8c1fa4fe1935da1f1dedd1b18f4b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593567"
---
# <a name="services-page-project-designer"></a>Strona usług, Projektant projektu

Usługi aplikacji klienckich [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] zapewniają uproszczony dostęp do usług logowania, ról i profili z aplikacji Windows Forms i Windows Presentation Foundation (WPF). Za pomocą strony **Usługi** **projektanta projektu** można włączyć i skonfigurować usługi aplikacji klienckich dla projektu.

Za pomocą usług aplikacji klienckich można używać scentralizowanego serwera do uwierzytelniania użytkowników, określania przypisanej roli lub ról każdego użytkownika oraz przechowywania ustawień aplikacji dla poszczególnych użytkowników, które można udostępniać w sieci. Aby uzyskać więcej informacji, zobacz [Usługi aplikacji klienta](/dotnet/framework/common-client-technologies/client-application-services).

Aby uzyskać dostęp do strony **Usługi,** wybierz węzeł projektu w **Eksploratorze rozwiązań,** a następnie w menu **Projekt** kliknij polecenie **Właściwości.** Po wyświetleniu **projektanta projektu** kliknij kartę **Usługi.**

## <a name="task-list"></a>Lista zadań

[Instrukcje: konfigurowanie usług aplikacji klienckich](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Lista elementów UI

 **Konfiguracja**

Ta kontrolka nie jest edytowalna na tej stronie. Aby uzyskać opis tego formantu, zobacz [Strona kompilacji, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) lub [Strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platforma**

Ta kontrolka nie jest edytowalna na tej stronie. Aby uzyskać opis tego formantu, zobacz [Strona kompilacji, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) lub [Strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Włączanie usług aplikacji klienckich**

Wybierz, aby włączyć usługi aplikacji klienckiej. Aby korzystać z usług aplikacji klienckich, należy określić lokalizacje usług na stronie **Usługi.**

 **Korzystanie z uwierzytelniania systemu Windows**

Wskazuje, że dostawca uwierzytelniania będzie używał uwierzytelniania opartego na systemie Windows, czyli tożsamości dostarczonej przez system operacyjny Windows.

 **Korzystanie z uwierzytelniania formularzy**

Wskazuje, że dostawca uwierzytelniania będzie używał uwierzytelniania formularzy. Oznacza to, że aplikacja musi zapewnić interfejs użytkownika do logowania. Aby uzyskać więcej informacji, zobacz [Jak: Implementowanie logowania użytkownika za pomocą usług aplikacji klienta](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).

 **Lokalizacja usługi uwierzytelniania**

Używane tylko z uwierzytelnianiem formularzy. Określa lokalizację usługi uwierzytelniania.

 **Opcjonalnie: dostawca poświadczeń**

Używane tylko z uwierzytelnianiem formularzy. Wskazuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> implementację, której usługa uwierzytelniania będzie używać do wyświetlania `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> okna dialogowego logowania, gdy aplikacja wywołuje metodę i przekazuje puste ciągi lub `null` parametry. Jeśli to pole pozostanie puste, musisz przekazać prawidłową <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> nazwę użytkownika i hasło do metody. Należy określić dostawcę poświadczeń jako nazwę typu kwalifikowanego zestawu. Aby uzyskać więcej <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> informacji, zobacz i [Nazwy zespołów](/dotnet/framework/app-domains/assembly-names). W najprostszej formie nazwa typu kwalifikowanego zestawu wygląda podobnie do następującego przykładu:`MyNamespace.MyLoginClass, MyAssembly`

 **Lokalizacja usługi Role**

Określa lokalizację usługi ról.

 **Lokalizacja usługi ustawień sieci Web**

Określa lokalizację usługi profilu (ustawienia sieci Web).

 **Zaawansowane**

Otwiera [okno dialogowe Ustawienia zaawansowane dla usług,](../../ide/reference/advanced-settings-for-services-dialog-box.md)za pomocą którego można zastąpić zachowanie domyślne. Na przykład można użyć tego okna dialogowego, aby określić bazę danych dla magazynu w trybie offline zamiast lokalnego systemu plików. Aby uzyskać więcej informacji, zobacz [Okno dialogowe Ustawienia zaawansowane usług](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Zobacz też

- [Usługi aplikacji klienckich](/dotnet/framework/common-client-technologies/client-application-services)
- [Zaawansowane ustawienia dla usług — Okno dialogowe](../../ide/reference/advanced-settings-for-services-dialog-box.md)
- [Instrukcje: konfigurowanie usług aplikacji klienckich](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
- [Strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)
