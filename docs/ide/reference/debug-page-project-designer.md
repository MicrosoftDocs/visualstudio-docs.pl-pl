---
title: Strona debugowania, Projektant projektu
ms.date: 06/27/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1f54485a4dd47b0aec4401f6cdfb39072e9f8cf
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461407"
---
# <a name="debug-page-project-designer"></a>Strona debugowania, Projektant projektu

Strona **Debuguj** **projektanta projektu** służy do ustawiania właściwości zachowania debugowania w Visual Basic lub C# projekcie.

Aby uzyskać dostęp do strony **debugowanie** , wybierz węzeł projektu w **Eksplorator rozwiązań**. W menu **projekt** wybierz pozycję  **\<ProjectName > Właściwości**. Gdy pojawi się **Projektant projektu** , kliknij kartę **debugowanie** .

> [!NOTE]
> W tym temacie nie ma zastosowania do aplikacji platformy uniwersalnej systemu Windows. Zobacz [Rozpoczynanie sesji debugowania (VB, C# C++ i XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) dla aplikacji platformy UWP.

## <a name="configuration-and-platform"></a>Konfiguracja i platforma

Poniższe opcje pozwalają wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.

**Konfiguracja**

Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Ustawienia mogą być **debugowane** (ustawienie domyślne), **wydanie**lub **wszystkie konfiguracje**.

**Platformach**

Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Dostępne opcje to: **dowolny procesor** (domyślny), **x64**i **x86**.

## <a name="start-action"></a>Uruchom akcję

**Akcja uruchamiania** wskazuje element, który ma zostać uruchomiony podczas debugowania aplikacji: projekt, program niestandardowy, adres URL lub wartość Nothing. Domyślnie ta opcja jest ustawiona na **Uruchom projekt**. Ustawienie **akcji Rozpocznij** na stronie **Debuguj** określa `StartAction` wartość właściwości.

**Uruchom projekt**

Wybierz tę opcję, aby określić, że plik wykonywalny (dla projektów aplikacji i aplikacji konsolowej systemu Windows) powinien być uruchamiany, gdy aplikacja jest debugowana. Ta opcja jest domyślnie wybrana.

**Uruchom program zewnętrzny**

Wybierz tę opcję, aby określić, że określony program ma być uruchamiany podczas debugowania aplikacji.

**Uruchom przeglądarkę z adresem URL**

Wybierz tę opcję, aby określić, że określony adres URL ma być dostępny podczas debugowania aplikacji.

## <a name="start-options"></a>Opcje uruchamiania

**Argumenty wiersza polecenia**

W tym polu tekstowym wprowadź argumenty wiersza polecenia, które mają być używane na potrzeby debugowania.

**Katalog roboczy**

W tym polu tekstowym wprowadź katalog, z którego zostanie uruchomiony projekt. Lub kliknij przycisk przeglądania ( **...** ), aby wybrać katalog.

**Użyj maszyny zdalnej**

Aby debugować aplikację z komputera zdalnego, zaznacz to pole wyboru, a następnie w polu tekstowym wprowadź ścieżkę do komputera zdalnego.

## <a name="debugger-engines"></a>Aparaty debugera

**Włącz debugowanie kodu natywnego**

Ta opcja określa, czy Debugowanie kodu natywnego jest obsługiwane. Zaznacz to pole wyboru, jeśli tworzysz wywołania do obiektów COM lub uruchamiasz niestandardowy program pisany w kodzie natywnym, który wywołuje projekt i musisz debugować kod natywny. Wyczyść to pole wyboru, aby wyłączyć debugowanie kodu niezarządzanego. To pole wyboru jest domyślnie wyczyszczone.

**Włącz debugowanie SQL Server**

Zaznacz lub wyczyść to pole wyboru, aby włączyć lub wyłączyć debugowanie procedur SQL z aplikacji Visual Basic. To pole wyboru jest domyślnie wyczyszczone.

## <a name="see-also"></a>Zobacz także

- [Pierwsze spojrzenie na debugera](../../debugger/debugger-feature-tour.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C#](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Instrukcje: Debugowanie aplikacji ClickOnce przy użyciu ograniczonych uprawnień](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Instrukcje: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md)