---
title: Okno dialogowe Ustawienia zaawansowane dla usług | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1a021475df1ade9bb6220612aad666d503c19cb8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651716"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Zaawansowane ustawienia dla usług — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usługi aplikacji klienta zapewniają uproszczony dostęp do [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] logowania, ról i usług profilów z aplikacji Windows Forms i Windows Presentation Foundation (WPF). Aby skonfigurować usługi aplikacji klienta, można użyć strony **usługi** w **projektancie projektu** . Aby uzyskać więcej informacji o stronie **usług** , zobacz [stronę usług, Projektant projektu](../../ide/reference/services-page-project-designer.md).

 Za pomocą okna dialogowego **Ustawienia zaawansowane dla usług** na stronie **usługi** w **projektancie projektu** można skonfigurować zaawansowane ustawienia dla usług aplikacji klienta. Korzystając z tych ustawień, można zastąpić niektóre domyślne zachowania usługi aplikacji, aby włączyć mniej typowe scenariusze. Aby uzyskać więcej informacji, zobacz [usługi aplikacji klienta](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).

 Aby uzyskać dostęp do okna dialogowego **Ustawienia zaawansowane dla usług** , wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie kliknij pozycję **Właściwości** w menu **projekt** . Gdy zostanie wyświetlony **Projektant projektu** , kliknij kartę **usługi** , a następnie kliknij przycisk **Zaawansowane** . Ten przycisk zostanie wyłączony do momentu włączenia usług aplikacji klienta.

## <a name="task-list"></a>Lista zadań
 [Instrukcje: konfigurowanie usług aplikacji klienckich](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)

 [Instrukcje: korzystanie z Usługi aplikacji klienta w trybie offline](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)

## <a name="uielement-list"></a>Lista elementów UI
 **Zapisywanie skrótu hasła lokalnie w celu włączenia logowania w trybie offline** Określa, czy zaszyfrowana postać hasła użytkownika będzie buforowana lokalnie, aby umożliwić użytkownikowi zalogowanie się, gdy aplikacja działa w trybie offline. Aby uzyskać więcej informacji, zobacz [How to: Work offline with Client usługi aplikacji](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38). Ta opcja jest domyślnie wybrana.

 **Wymagaj od użytkowników ponownego zalogowania się za każdym razem, gdy plik cookie serwera wygaśnie** Określa, czy wcześniej uwierzytelnieni użytkownicy są automatycznie uwierzytelniani, gdy aplikacja uzyskuje dostęp do ról lub usługi profilu, a plik cookie uwierzytelniania serwera wygasł. Wybierz tę opcję, aby odmówić dostępu do usług aplikacji i wymagać jawnego ponownego uwierzytelnienia po wygaśnięciu pliku cookie. Jest to przydatne w przypadku aplikacji wdrożonych w lokalizacjach publicznych, aby upewnić się, że użytkownicy, którzy opuszczają aplikację po jej użyciu, nie będą uwierzytelniani przez czas nieokreślony. Ta opcja jest domyślnie wyczyszczona.

 **Limit czasu pamięci podręcznej usługi roli** Określa czas, przez jaki dostawca roli klienta będzie używał wartości roli w pamięci podręcznej zamiast uzyskiwania dostępu do usługi ról. Ustaw ten przedział czasu na małą wartość, gdy role są aktualizowane często lub do większej wartości, gdy role są aktualizowane rzadko. Wartość domyślna to jeden dzień.

 Dostawca roli uzyskuje dostęp do buforowanych wartości ról lub usługi ról po wywołaniu metody <xref:System.Web.Security.RolePrincipal.IsInRole%2A>. Aby programowo wyczyścić pamięć podręczną i wymusić dostęp tej metody do usługi zdalnej, wywołaj metodę <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>.

 **Użyj niestandardowych parametrów połączenia** Określa, czy dostawcy usług klienta będą używać niestandardowego magazynu danych dla lokalnej pamięci podręcznej. Domyślnie dostawcy usług będą używać lokalnego systemu plików dla pamięci podręcznej. Wybranie tej opcji spowoduje automatyczne wypełnienie pola tekstowego domyślnymi parametrami połączenia. Można zachować domyślne parametry połączenia, aby automatycznie generować i korzystać z bazy danych SQL Server Compact Edition, lub określić parametry połączenia do istniejącej bazy danych SQL Server. Aby uzyskać więcej informacji, zobacz [How to: Configure Client usługi aplikacji](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8). Ta opcja jest domyślnie wyczyszczona.

## <a name="see-also"></a>Zobacz też
 Strona usługi [usługi aplikacji klienta](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e) [, Projektant projektu](../../ide/reference/services-page-project-designer.md) [How to: Configure Client usługi aplikacji](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8) [how to: Work offline with Client usługi aplikacji](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)
