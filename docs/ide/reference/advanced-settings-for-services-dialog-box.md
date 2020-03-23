---
title: Zaawansowane ustawienia dla usług — Okno dialogowe
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
ms.openlocfilehash: 967e99102f3b88e82a5466e7ce8d2cac2412d286
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585681"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Zaawansowane ustawienia dla usług — Okno dialogowe
Usługi aplikacji klienckich [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] zapewniają uproszczony dostęp do usług logowania, ról i profili z aplikacji Windows Forms i Windows Presentation Foundation (WPF). Za pomocą strony **Usługi** w **projektancie projektu** można skonfigurować usługi aplikacji klienckich. Aby uzyskać więcej informacji na temat strony **Usługi,** zobacz [Strona usług, Projektant projektu](../../ide/reference/services-page-project-designer.md).

Użyj okna dialogowego **Ustawienia zaawansowane dla usług** na stronie **Usługi** w **Projektancie projektu,** aby skonfigurować ustawienia zaawansowane dla usług aplikacji klienckich. Za pomocą tych ustawień, można zastąpić niektóre domyślne zachowania usługi aplikacji, aby włączyć mniej typowych scenariuszy. Aby uzyskać więcej informacji, zobacz [Usługi aplikacji klienta](/dotnet/framework/common-client-technologies/client-application-services).

Aby uzyskać dostęp do okna dialogowego **Ustawienia zaawansowane dla usług,** wybierz węzeł projektu w **Eksploratorze rozwiązań,** a następnie w menu **Projekt** kliknij polecenie **Właściwości.** Po wyświetleniu **projektanta projektu** kliknij kartę **Usługi,** a następnie kliknij przycisk **Zaawansowane.** Ten przycisk zostanie wyłączony, dopóki nie włączysz usług aplikacji klienckich.

## <a name="task-list"></a>Lista zadań

- [Instrukcje: konfigurowanie usług aplikacji klienckich](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Lista elementów UI

 **Zapisywanie skrótu hasła lokalnie w celu włączenia logowania w trybie offline** Określa, czy zaszyfrowana forma hasła użytkownika będzie buforowana lokalnie, aby umożliwić użytkownikowi logowanie się, gdy aplikacja jest w trybie offline. Ta opcja jest domyślnie wybrana.

 **Wymagaj od użytkowników ponownego zalogowania się przy każdym wygaśnięciu pliku cookie serwera** Określa, czy wcześniej uwierzytelnieni użytkownicy są automatycznie reauthenticated, gdy aplikacja uzyskuje dostęp do ról lub usługi profilu i plik cookie uwierzytelniania serwera wygasła. Wybierz tę opcję, aby odmówić dostępu do usług aplikacji i wymagać jawnego ponownego uwierzytelnienia po wygaśnięciu pliku cookie. Jest to przydatne w przypadku aplikacji wdrożonych w lokalizacjach publicznych, aby upewnić się, że użytkownicy, którzy opuszczają aplikację po użyciu, nie pozostaną uwierzytelnieni przez czas nieokreślony. Ta opcja jest domyślnie wyczyszczona.

 **Limit czasu pamięci podręcznej usługi roli** Określa czas, przez przez który dostawca roli klienta będzie używał buforowanych wartości ról zamiast uzyskiwania dostępu do usługi ról. Ustaw ten przedział czasu na małą wartość, gdy role są często aktualizowane lub do większej wartości, gdy role są aktualizowane rzadko. Wartość domyślna to jeden dzień.

Dostawca roli uzyskuje dostęp do wartości ról buforowanych lub <xref:System.Web.Security.RolePrincipal.IsInRole%2A> usługi ról podczas wywoływania metody. Aby programowo wyczyścić pamięć podręczną i wymusić dostęp <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> do usługi zdalnej, należy wywołać metodę.

 **Użyj niestandardowego ciągu połączenia** Określa, czy dostawcy usług klienckich będą używać niestandardowego magazynu danych dla lokalnej pamięci podręcznej. Domyślnie dostawcy usług będą używać lokalnego systemu plików dla pamięci podręcznej. Wybranie tej opcji spowoduje automatyczne wypełnienie pola tekstowego domyślnym ciągiem połączenia. Domyślny ciąg połączenia można zachować w celu automatycznego generowania i używania bazy danych programu SQL Server Compact Edition lub można określić parametry połączenia z istniejącą bazą danych programu SQL Server. Aby uzyskać więcej informacji, zobacz [Jak: Konfigurowanie usług aplikacji klienckich](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services). Ta opcja jest domyślnie wyczyszczona.

## <a name="see-also"></a>Zobacz też

- [Usługi aplikacji klienckich](/dotnet/framework/common-client-technologies/client-application-services)
- [Strona usług, Projektant projektu](../../ide/reference/services-page-project-designer.md)
- [Instrukcje: konfigurowanie usług aplikacji klienckich](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
