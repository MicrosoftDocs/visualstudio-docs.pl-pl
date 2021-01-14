---
title: Strona debugowania, Projektant projektu
description: Strona Debuguj projektanta projektu służy do ustawiania właściwości debugowania w projekcie Visual Basic lub C#. Zobacz ten artykuł, aby zapoznać się z opisami ustawień.
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8567b762e9858205e3ca8d6aafa8a3dba17a90fe
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205778"
---
# <a name="debug-page-project-designer"></a>Strona debugowania, Projektant projektu

Strona **Debuguj** **projektanta projektu** służy do ustawiania właściwości zachowania debugowania w projekcie Visual Basic lub C#.

Aby uzyskać dostęp do strony **debugowanie** , wybierz węzeł projektu w **Eksplorator rozwiązań**. W menu **projekt** wybierz polecenie **\<ProjectName> Właściwości**. Gdy pojawi się **Projektant projektu** , kliknij kartę **debugowanie** .

> [!NOTE]
> Ten temat nie dotyczy aplikacji platformy UWP. Zobacz [Rozpoczynanie sesji debugowania (VB, C#, C++ i XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) dla aplikacji platformy UWP.

## <a name="configuration-and-platform"></a>Konfiguracja i platforma

Poniższe opcje pozwalają wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.

**Konfiguracja**

Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Ustawienia mogą być **debugowane** (ustawienie domyślne), **wydanie** lub **wszystkie konfiguracje**.

**Platforma**

Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Dostępne opcje to: **dowolny procesor** (domyślny), **x64** i **x86**.

## <a name="start-action"></a>Uruchom akcję

**Akcja uruchamiania** wskazuje element, który ma zostać uruchomiony podczas debugowania aplikacji: projekt, program niestandardowy, adres URL lub wartość Nothing. Domyślnie ta opcja jest ustawiona na **Uruchom projekt**. Ustawienie **akcji Rozpocznij** na stronie **Debuguj** określa wartość `StartAction` właściwości.

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

W tym polu tekstowym wprowadź katalog, z którego zostanie uruchomiony projekt. Lub kliknij przycisk przeglądania (**...**), aby wybrać katalog.

**Użyj maszyny zdalnej**

Aby debugować aplikację z komputera zdalnego, zaznacz to pole wyboru, a następnie w polu tekstowym wprowadź ścieżkę do komputera zdalnego.

## <a name="debugger-engines"></a>Aparaty debugera

**Włącz debugowanie kodu natywnego**

Ta opcja określa, czy Debugowanie kodu natywnego jest obsługiwane. Zaznacz to pole wyboru, jeśli tworzysz wywołania do obiektów COM lub uruchamiasz niestandardowy program pisany w kodzie natywnym, który wywołuje projekt i musisz debugować kod natywny. Wyczyść to pole wyboru, aby wyłączyć debugowanie kodu niezarządzanego. To pole wyboru jest domyślnie wyczyszczone.

**Włącz debugowanie SQL Server**

Zaznacz lub wyczyść to pole wyboru, aby włączyć lub wyłączyć debugowanie procedur SQL z aplikacji Visual Basic. To pole wyboru jest domyślnie wyczyszczone.

## <a name="see-also"></a>Zobacz też

- [Pierwsze spojrzenie na debugera](../../debugger/debugger-feature-tour.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C#](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Zabezpieczanie aplikacji ClickOnce](../../deployment/securing-clickonce-applications.md)
- [Porady: tworzenie i edycja konfiguracji](../../ide/how-to-create-and-edit-configurations.md)
