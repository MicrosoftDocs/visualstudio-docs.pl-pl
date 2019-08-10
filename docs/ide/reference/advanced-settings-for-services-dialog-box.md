---
title: Zaawansowane ustawienia dla usług — Okno dialogowe
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7f599b4448fe39bf8c0d82d030f5f1173f28699
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919329"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Zaawansowane ustawienia dla usług — Okno dialogowe
Usługi aplikacji klienta zapewniają uproszczony dostęp [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] do danych logowania, ról i usług profilów z aplikacji Windows Forms i Windows Presentation Foundation (WPF). Aby skonfigurować usługi aplikacji klienta, można użyć strony **usługi** w **projektancie projektu** . Aby uzyskać więcej informacji o stronie **usług** , zobacz [stronę usług, Projektant projektu](../../ide/reference/services-page-project-designer.md).

Za pomocą okna dialogowego **Ustawienia zaawansowane dla usług** na stronie **usługi** w **projektancie projektu** można skonfigurować zaawansowane ustawienia dla usług aplikacji klienta. Korzystając z tych ustawień, można zastąpić niektóre domyślne zachowania usługi aplikacji, aby włączyć mniej typowe scenariusze. Aby uzyskać więcej informacji, zobacz [usługi aplikacji klienta](/dotnet/framework/common-client-technologies/client-application-services).

Aby uzyskać dostęp do okna dialogowego **Ustawienia zaawansowane dla usług** , wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie kliknij pozycję **Właściwości** w menu **projekt** . Gdy zostanie wyświetlony **Projektant projektu** , kliknij kartę **usługi** , a następnie kliknij przycisk **Zaawansowane** . Ten przycisk zostanie wyłączony do momentu włączenia usług aplikacji klienta.

## <a name="task-list"></a>Lista zadań

- [Instrukcje: Konfigurowanie Usługi aplikacji klienta](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Lista elementów UI

 **Zapisywanie skrótu hasła lokalnie w celu włączenia logowania w trybie offline** Określa, czy zaszyfrowana postać hasła użytkownika będzie buforowana lokalnie, aby umożliwić użytkownikowi zalogowanie się, gdy aplikacja działa w trybie offline. Ta opcja jest domyślnie wybrana.

 **Wymagaj od użytkowników ponownego zalogowania się za każdym razem, gdy plik cookie serwera wygaśnie** Określa, czy wcześniej uwierzytelnieni użytkownicy są automatycznie uwierzytelniani, gdy aplikacja uzyskuje dostęp do ról lub usługi profilu, a plik cookie uwierzytelniania serwera wygasł. Wybierz tę opcję, aby odmówić dostępu do usług aplikacji i wymagać jawnego ponownego uwierzytelnienia po wygaśnięciu pliku cookie. Jest to przydatne w przypadku aplikacji wdrożonych w lokalizacjach publicznych, aby upewnić się, że użytkownicy, którzy opuszczają aplikację po jej użyciu, nie będą uwierzytelniani przez czas nieokreślony. Ta opcja jest domyślnie wyczyszczona.

 **Limit czasu pamięci podręcznej usługi roli** Określa czas, przez jaki dostawca roli klienta będzie używał wartości roli w pamięci podręcznej zamiast uzyskiwania dostępu do usługi ról. Ustaw ten przedział czasu na małą wartość, gdy role są aktualizowane często lub do większej wartości, gdy role są aktualizowane rzadko. Wartość domyślna to jeden dzień.

Dostawca roli uzyskuje dostęp do buforowanych wartości ról lub usługi ról po wywołaniu <xref:System.Web.Security.RolePrincipal.IsInRole%2A> metody. Aby programowo wyczyścić pamięć podręczną i wymusić dostęp tej metody do usługi zdalnej, <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> Wywołaj metodę.

 **Użyj niestandardowych parametrów połączenia** Określa, czy dostawcy usług klienta będą używać niestandardowego magazynu danych dla lokalnej pamięci podręcznej. Domyślnie dostawcy usług będą używać lokalnego systemu plików dla pamięci podręcznej. Wybranie tej opcji spowoduje automatyczne wypełnienie pola tekstowego domyślnymi parametrami połączenia. Można zachować domyślne parametry połączenia, aby automatycznie generować i korzystać z bazy danych SQL Server Compact Edition, lub określić parametry połączenia do istniejącej bazy danych SQL Server. Aby uzyskać więcej informacji, zobacz [jak: Skonfiguruj Usługi aplikacji](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)klienta. Ta opcja jest domyślnie wyczyszczona.

## <a name="see-also"></a>Zobacz także

- [Usługi aplikacji klienckich](/dotnet/framework/common-client-technologies/client-application-services)
- [Strona usług, Projektant projektu](../../ide/reference/services-page-project-designer.md)
- [Instrukcje: Konfigurowanie Usługi aplikacji klienta](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)