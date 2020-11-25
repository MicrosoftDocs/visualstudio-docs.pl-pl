---
title: Zaawansowane ustawienia dla usług — Okno dialogowe
description: Dowiedz się, jak skonfigurować zaawansowane ustawienia usług aplikacji klienta przy użyciu funkcji zaawansowane ustawienia usług.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59ad28dd6890effbac00282a0e9bc388b4191139
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871317"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Zaawansowane ustawienia dla usług — Okno dialogowe
Usługi aplikacji klienta zapewniają uproszczony dostęp do danych [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] logowania, ról i usług profilów z aplikacji Windows Forms i Windows Presentation Foundation (WPF). Aby skonfigurować usługi aplikacji klienta, można użyć strony **usługi** w **projektancie projektu** . Aby uzyskać więcej informacji o stronie **usług** , zobacz [stronę usług, Projektant projektu](../../ide/reference/services-page-project-designer.md).

Za pomocą okna dialogowego **Ustawienia zaawansowane dla usług** na stronie **usługi** w **projektancie projektu** można skonfigurować zaawansowane ustawienia dla usług aplikacji klienta. Korzystając z tych ustawień, można zastąpić niektóre domyślne zachowania usługi aplikacji, aby włączyć mniej typowe scenariusze. Aby uzyskać więcej informacji, zobacz [usługi aplikacji klienta](/dotnet/framework/common-client-technologies/client-application-services).

Aby uzyskać dostęp do okna dialogowego **Ustawienia zaawansowane dla usług** , wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie kliknij pozycję **Właściwości** w menu **projekt** . Gdy zostanie wyświetlony **Projektant projektu** , kliknij kartę **usługi** , a następnie kliknij przycisk **Zaawansowane** . Ten przycisk zostanie wyłączony do momentu włączenia usług aplikacji klienta.

## <a name="task-list"></a>Lista zadań

- [Instrukcje: konfigurowanie usług aplikacji klienckich](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Lista elementów UI

 **Zapisywanie skrótu hasła lokalnie w celu włączenia logowania w trybie offline** Określa, czy zaszyfrowana postać hasła użytkownika będzie buforowana lokalnie, aby umożliwić użytkownikowi zalogowanie się, gdy aplikacja działa w trybie offline. Ta opcja jest domyślnie wybrana.

 **Wymagaj od użytkowników ponownego zalogowania się za każdym razem, gdy plik cookie serwera wygaśnie** Określa, czy wcześniej uwierzytelnieni użytkownicy są automatycznie uwierzytelniani, gdy aplikacja uzyskuje dostęp do ról lub usługi profilu, a plik cookie uwierzytelniania serwera wygasł. Wybierz tę opcję, aby odmówić dostępu do usług aplikacji i wymagać jawnego ponownego uwierzytelnienia po wygaśnięciu pliku cookie. Jest to przydatne w przypadku aplikacji wdrożonych w lokalizacjach publicznych, aby upewnić się, że użytkownicy, którzy opuszczają aplikację po jej użyciu, nie będą uwierzytelniani przez czas nieokreślony. Ta opcja jest domyślnie wyczyszczona.

 **Limit czasu pamięci podręcznej usługi roli** Określa czas, przez jaki dostawca roli klienta będzie używał wartości roli w pamięci podręcznej zamiast uzyskiwania dostępu do usługi ról. Ustaw ten przedział czasu na małą wartość, gdy role są aktualizowane często lub do większej wartości, gdy role są aktualizowane rzadko. Wartość domyślna to jeden dzień.

Dostawca roli uzyskuje dostęp do buforowanych wartości ról lub usługi ról po wywołaniu <xref:System.Web.Security.RolePrincipal.IsInRole%2A> metody. Aby programowo wyczyścić pamięć podręczną i wymusić dostęp tej metody do usługi zdalnej, wywołaj <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> metodę.

 **Użyj niestandardowych parametrów połączenia** Określa, czy dostawcy usług klienta będą używać niestandardowego magazynu danych dla lokalnej pamięci podręcznej. Domyślnie dostawcy usług będą używać lokalnego systemu plików dla pamięci podręcznej. Wybranie tej opcji spowoduje automatyczne wypełnienie pola tekstowego domyślnymi parametrami połączenia. Można zachować domyślne parametry połączenia, aby automatycznie generować i korzystać z bazy danych SQL Server Compact Edition, lub określić parametry połączenia do istniejącej bazy danych SQL Server. Aby uzyskać więcej informacji, zobacz [How to: Configure Client usługi aplikacji](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services). Ta opcja jest domyślnie wyczyszczona.

## <a name="see-also"></a>Zobacz także

- [Usługi aplikacji klienckich](/dotnet/framework/common-client-technologies/client-application-services)
- [Strona usług, Projektant projektu](../../ide/reference/services-page-project-designer.md)
- [Instrukcje: konfigurowanie usług aplikacji klienckich](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
