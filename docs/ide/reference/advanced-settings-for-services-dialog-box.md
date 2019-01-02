---
title: Zaawansowane ustawienia dla usług — Okno dialogowe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 251a78ebe56a9ba2c88444da879970c590ece029
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917228"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Zaawansowane ustawienia dla usług — Okno dialogowe
Usługi aplikacji klienta zapewniają uproszczony dostęp do [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] logowania, ról i usług profilu z aplikacji Windows Forms i Windows Presentation Foundation (WPF). Możesz użyć **usług** strony w **projektanta projektu** do skonfigurowania usług aplikacji klienta. Aby uzyskać więcej informacji na temat **usług** stronie, zobacz [Strona usług, Projektant projektu](../../ide/reference/services-page-project-designer.md).

 Użyj **ustawienia zaawansowane dla usług** okna dialogowego **usług** strony w **projektanta projektu** Aby skonfigurować ustawienia zaawansowane dla usług aplikacji klienta. Za pomocą tych ustawień, można zastąpić niektóre zachowania domyślne aplikacji usługa mniej typowych scenariuszy. Aby uzyskać więcej informacji, zobacz [usług aplikacji klienta](/dotnet/framework/common-client-technologies/client-application-services).

 Aby uzyskać dostęp do **Zaawansowane ustawienia dla usług** okna dialogowego wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie kliknij przycisk **właściwości** na **projektu**  menu. Gdy **projektanta projektu** pojawi się, kliknij przycisk **usług** kartę, a następnie kliknij przycisk **zaawansowane** przycisk. Ten przycisk, zostaną wyłączone do czasu włączenia usługi aplikacji klienta.

## <a name="task-list"></a>Lista zadań

- [Instrukcje: Konfigurowanie usług aplikacji klienta](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Lista elementów UI

 **Zapisz wartość skrótu hasła lokalnie, aby włączyć logowanie w trybie offline** Określa, czy zaszyfrowane hasło użytkownika będą buforowane lokalnie do użytkownika zalogować się, gdy aplikacja jest w trybie offline. Ta opcja jest domyślnie wybrana.

 **Wymagać od użytkowników zalogować się ponownie przy każdym wygasa plik cookie serwera** Określa, czy wcześniej uwierzytelnieni użytkownicy są automatycznie ponownie uwierzytelniany gdy aplikacja uzyskuje dostęp do ról lub usługę profilu i uwierzytelniania serwera plik cookie utracił ważność. Wybierz tę opcję, aby odmówić dostępu do usług aplikacji i wymaga jawnego ponownego uwierzytelnienia, po wygaśnięciu pliku cookie. Jest to przydatne w przypadku aplikacji wdrożonych w miejscach publicznych upewnić się, czy użytkownicy, którzy aplikacja działa po użyciu nie pozostanie uwierzytelniony przez czas nieokreślony. Ta opcja jest domyślnie wyczyszczone.

 **Limit czasu pamięci podręcznej usługi roli** określa ilość czasu, użyje dostawcy roli klienta pamięci podręcznej wartości roli zamiast uzyskiwanie dostępu do usługi ról. Ustaw dany interwał czasu małej wartości, gdy role są aktualizowane często lub większej wartości role są rzadko aktualizowane. Wartość domyślna to jeden dzień.

 Dostawcy ról uzyskuje dostęp do wartości pamięci podręcznej roli lub usługi ról podczas wywoływania <xref:System.Web.Security.RolePrincipal.IsInRole%2A> metody. Aby programowo wyczyścić pamięć podręczną i wymusić tę metodę w celu uzyskania dostępu do usługi zdalnej, należy wywołać <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> metody.

 **Użyj niestandardowego ciągu połączenia** Określa, czy dostawcy usług klienta będzie używać niestandardowego magazynu danych dla lokalnej pamięci podręcznej. Domyślnie dostawców usług użyje lokalnego systemu plików w pamięci podręcznej. Wybranie tej opcji automatycznie spowoduje wypełnienie pola tekstowego przy użyciu domyślne parametry połączenia. Możesz zachować domyślne parametry połączenia, aby automatycznie generować i korzystania z bazy danych programu SQL Server Compact Edition, lub można określić parametry połączenia do istniejącej bazy danych programu SQL Server. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie usług aplikacji klienckich](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services). Ta opcja jest domyślnie wyczyszczone.

## <a name="see-also"></a>Zobacz także

- [Usługi aplikacji klienckich](/dotnet/framework/common-client-technologies/client-application-services)
- [Strona usług, Projektant projektu](../../ide/reference/services-page-project-designer.md)
- [Instrukcje: Konfigurowanie usług aplikacji klienta](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)