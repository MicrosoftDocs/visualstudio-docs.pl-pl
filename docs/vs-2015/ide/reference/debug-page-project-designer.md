---
title: Strona debugowania, Projektant projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 006662d7c07ba0498fff4617eca3fdc7c631d37b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660784"
---
# <a name="debug-page-project-designer"></a>Strona debugowania, Projektant projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!WARNING]
> Ten temat nie dotyczy aplikacji ze sklepu Windows. Zobacz [Rozpoczynanie sesji debugowania (VB, C# C++ i XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) w centrum deweloperów systemu Windows.

 Strona **Debuguj** **projektanta projektu** służy do ustawiania właściwości zachowania debugowania w Visual Basic lub C# projekcie.

 Aby uzyskać dostęp do strony **debugowanie** , wybierz węzeł projektu w **Eksplorator rozwiązań**. W menu **projekt** wybierz pozycję właściwości _ProjectName_. Gdy pojawi się **Projektant projektu** , kliknij kartę **debugowanie** .

## <a name="configuration-and-platform"></a>Konfiguracja i platforma
 Poniższe opcje pozwalają wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.

 **Konfiguracja** Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Ustawienia mogą być **debugowane** (ustawienie domyślne), **wydanie**lub **wszystkie konfiguracje**. Aby uzyskać więcej informacji, zobacz [debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Platforma** Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Dostępne opcje to: **dowolny procesor** (domyślny), **x64**i **x86**. Aby uzyskać więcej informacji, zobacz [debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="start-action"></a>Uruchom akcję
 **Akcja uruchamiania** wskazuje element, który ma zostać uruchomiony podczas debugowania aplikacji: projekt, program niestandardowy, adres URL lub wartość Nothing. Domyślnie ta opcja jest ustawiona na **Uruchom projekt**. Ustawienie **akcji Rozpocznij** na stronie **Debuguj** określa wartość właściwości `StartAction`.

 **Uruchom projekt** Wybierz tę opcję, aby określić, że plik wykonywalny (dla projektów aplikacji i aplikacji konsolowej systemu Windows) powinien być uruchamiany, gdy aplikacja jest debugowana. Ta opcja jest domyślnie wybrana.

 **Uruchom program zewnętrzny** Wybierz tę opcję, aby określić, że określony program ma być uruchamiany podczas debugowania aplikacji.

 **Uruchom przeglądarkę z adresem URL** Wybierz tę opcję, aby określić, że określony adres URL ma być dostępny podczas debugowania aplikacji.

## <a name="start-options"></a>Opcje uruchamiania
 **Argumenty wiersza polecenia** W tym polu tekstowym wprowadź argumenty wiersza polecenia, które mają być używane na potrzeby debugowania.

 **Katalog roboczy** W tym polu tekstowym wprowadź katalog, z którego zostanie uruchomiony projekt. Lub kliknij przycisk przeglądania ( **...** ), aby wybrać katalog.

 **Użyj maszyny zdalnej** Aby debugować aplikację z komputera zdalnego, zaznacz to pole wyboru, a następnie w polu tekstowym wprowadź ścieżkę do komputera zdalnego.

## <a name="enable-debuggers"></a>Włącz debugery
 **Włącz debugowanie kodu niezarządzanego** Ta opcja określa, czy Debugowanie kodu natywnego jest obsługiwane. Zaznacz to pole wyboru, jeśli tworzysz wywołania do obiektów COM lub uruchamiasz niestandardowy program pisany w kodzie natywnym, który wywołuje projekt i musisz debugować kod natywny. Wyczyść to pole wyboru, aby wyłączyć debugowanie kodu niezarządzanego. To pole wyboru jest domyślnie wyczyszczone.

 **Włącz debugowanie SQL Server** Zaznacz lub wyczyść to pole wyboru, aby włączyć lub wyłączyć debugowanie procedur SQL z aplikacji Visual Basic. To pole wyboru jest domyślnie wyczyszczone.

 **Włącz proces hostingu programu Visual Studio** Zaznacz to pole wyboru, aby włączyć proces hostingu programu Visual Studio. To pole wyboru jest domyślnie zaznaczone. Aby uzyskać więcej informacji, zobacz [proces hostingu (vshost. exe)](../../ide/hosting-process-vshost-exe.md).

 Aby debugować w strefie zabezpieczeń, należy włączyć tę opcję i **debugować tę aplikację z wybranym zestawem uprawnień** w [oknie dialogowym Zaawansowane ustawienia zabezpieczeń](../../ide/reference/advanced-security-settings-dialog-box.md).

## <a name="see-also"></a>Zobacz też
 [Debugowanie w ustawieniach projektu programu Visual Studio](../../debugger/debugging-in-visual-studio.md) [dla C# konfiguracji debugowania](../../debugger/project-settings-for-csharp-debug-configurations.md) [Ustawienia projektu dla konfiguracji debugowania Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md) [Zarządzanie właściwościami debugowania](https://msdn.microsoft.com/92474d16-e7fe-4fac-9287-6bd6b3a7eb68) [jak: debugowanie aplikacji ClickOnce za pomocą Ograniczone uprawnienia](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md) [: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md)
