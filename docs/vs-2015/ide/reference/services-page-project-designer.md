---
title: Strona usług, Projektant projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 11e1cd997c76974e7b4b8771c0579c175469eca6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665485"
---
# <a name="services-page-project-designer"></a>Strona usług, Projektant projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usługi aplikacji klienta zapewniają uproszczony dostęp do danych [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] logowania, ról i usług profilów z aplikacji Windows Forms i Windows Presentation Foundation (WPF). Możesz użyć strony **usługi** **projektanta projektu** , aby włączyć i skonfigurować usługi aplikacji klienta dla projektu.

 Za pomocą usług aplikacji klienckich można używać scentralizowanego serwera do uwierzytelniania użytkowników, określania przypisanej roli lub ról poszczególnych użytkowników oraz przechowywania ustawień aplikacji dla poszczególnych użytkowników, które można udostępniać w sieci. Aby uzyskać więcej informacji, zobacz [usługi aplikacji klienta](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).

 Aby uzyskać dostęp do strony **usługi** , wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie kliknij pozycję **Właściwości** w menu **projekt** . Gdy zostanie wyświetlony **Projektant projektu** , kliknij kartę **usługi** .

> [!NOTE]
> Usługi aplikacji klienta wymagają pełnej wersji .NET Framework i nie są obsługiwane w profilu klienta .NET Framework. Jeśli pole wyboru **Włącz usługi aplikacji klienta** jest wyłączone, sprawdź, czy dla **platformy docelowej** jest ustawiona wartość .NET Framework 3,5 lub nowsza. Aby wyświetlić ustawienie **platformy docelowej** w języku C#, Otwórz projektanta projektu, a następnie kliknij stronę **aplikacji** . Aby wyświetlić ustawienie **platformy docelowej** w Visual Basic, Otwórz projektanta projektu, kliknij stronę **kompilacja** , a następnie kliknij pozycję **Zaawansowane opcje kompilacji**.

## <a name="task-list"></a>Lista zadań
 [Instrukcje: konfigurowanie usług aplikacji klienckich](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)

## <a name="uielement-list"></a>Lista elementów UI
 **Konfiguracja** Ta kontrolka nie jest edytowalna na tej stronie. Aby uzyskać opis tego formantu, zobacz [stronę Kompilacja, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) lub [stronę kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platforma** Ta kontrolka nie jest edytowalna na tej stronie. Aby uzyskać opis tego formantu, zobacz [stronę Kompilacja, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) lub [stronę kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Włącz usługi aplikacji klienta** Wybierz, aby włączyć usługi aplikacji klienta. Aby korzystać z usług aplikacji klienta, należy określić lokalizacje usług na stronie **usługi** .

 **Użyj uwierzytelniania systemu Windows** Wskazuje, że dostawca uwierzytelniania będzie używał uwierzytelniania opartego na systemie Windows, czyli tożsamości dostarczonej przez system operacyjny Windows.

 **Użyj uwierzytelniania formularzy** Wskazuje, że dostawca uwierzytelniania będzie korzystał z uwierzytelniania formularzy. Oznacza to, że aplikacja musi zapewnić interfejs użytkownika do logowania. Aby uzyskać więcej informacji, zobacz [jak: implementowanie logowania użytkownika przy użyciu usługi aplikacji klienta](https://msdn.microsoft.com/library/5431a671-eb02-4e18-a651-24764fccec9a).

 **Lokalizacja usługi uwierzytelniania** Używany tylko z uwierzytelnianiem formularzy. Określa lokalizację usługi uwierzytelniania.

 **Opcjonalne: Dostawca poświadczeń** Używany tylko z uwierzytelnianiem formularzy. Wskazuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> implementację, która będzie używana przez usługę uwierzytelniania do wyświetlania okna dialogowego logowania, gdy aplikacja wywołuje `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> metodę i przekazuje puste ciągi lub `null` parametry. Jeśli to pole pozostanie puste, należy przekazać do metody prawidłową nazwę użytkownika i hasło <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> . Należy określić dostawcę poświadczeń jako nazwę typu kwalifikowanego dla zestawu. Aby uzyskać więcej informacji, zobacz <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> i [nazwy zestawów](https://msdn.microsoft.com/library/8f8c2c90-f15d-400e-87e7-a757e4f04d0e). W najprostszej postaci nazwa typu kwalifikowana dla zestawu wygląda podobnie do poniższego przykładu: `MyNamespace.MyLoginClass, MyAssembly`

 **Lokalizacja usługi ról** Określa lokalizację usługi ról.

 **Lokalizacja usługi ustawień sieci Web** Określa lokalizację usługi profilu (Ustawienia sieci Web).

 **Zaawansowane** Otwiera okno [dialogowe Ustawienia zaawansowane dla usług](../../ide/reference/advanced-settings-for-services-dialog-box.md), za pomocą którego można przesłonić zachowanie domyślne. Na przykład można użyć tego okna dialogowego, aby określić bazę danych do przechowywania w trybie offline, zamiast korzystać z lokalnego systemu plików. Aby uzyskać więcej informacji, zobacz [okno dialogowe Ustawienia zaawansowane dla usług](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Zobacz też
 [Usługi aplikacji klienta](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e) [Ustawienia zaawansowane dla usług — okno dialogowe](../../ide/reference/advanced-settings-for-services-dialog-box.md) [instrukcje: Konfigurowanie klienta usługi aplikacji](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8) [Strona kompilacja, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) [Strona kompilacji, Projektant projektu (C#) —](../../ide/reference/build-page-project-designer-csharp.md) [wprowadzenie do projektanta projektu](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)
