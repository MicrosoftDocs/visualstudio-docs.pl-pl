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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2c3e7813e5e07a0fbb8f4ebf5838c883faa0fb8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595725"
---
# <a name="debug-page-project-designer"></a>Strona debugowania, Projektant projektu

Strona **Debugowanie** **projektanta projektu** służy do ustawiania właściwości zachowania debugowania w projekcie języka Visual Basic lub C#.

Aby uzyskać dostęp do strony **Debugowania,** wybierz węzeł projektu w **Eksploratorze rozwiązań**. W menu **Projekt** wybierz polecenie ** \<ProjectName> Properties**. Po wyświetleniu **projektanta projektu** kliknij kartę **Debugowanie.**

> [!NOTE]
> Ten temat nie dotyczy aplikacji platformy uniwersalnej systemu Windows. Zobacz [Uruchamianie sesji debugowania (VB, C#, C++ i XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) dla aplikacji platformy uniwersalnej systemu Windows.

## <a name="configuration-and-platform"></a>Konfiguracja i platforma

Poniższe opcje umożliwiają wybranie konfiguracji i platformy do wyświetlenia lub zmodyfikowania.

**Konfiguracja**

Określa ustawienia konfiguracji, które mają być wyświetlane lub modyfikowane. Ustawienia mogą być **Debugowanie** (domyślne), **Release**lub **Wszystkie konfiguracje**.

**Platforma**

Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Dostępne opcje mogą obejmować **dowolny procesor** (domyślny), **x64**i **x86**.

## <a name="start-action"></a>Rozpocznij akcję

**Akcja Start** wskazuje element, który ma być uruchamiany, gdy aplikacja jest debugowana: projekt, program niestandardowy, adres URL lub nic. Domyślnie ta opcja jest ustawiona na **Rozpocznij projekt**. Ustawienie **Akcja początkowa** na stronie **Debug** określa `StartAction` wartość właściwości.

**Rozpocznij projekt**

Wybierz tę opcję, aby określić, że plik wykonywalny (dla projektów aplikacji systemu Windows i aplikacji konsoli) powinien zostać uruchomiony, gdy aplikacja jest debugowana. Ta opcja jest domyślnie wybrana.

**Uruchamianie programu zewnętrznego**

Wybierz tę opcję, aby określić, że określony program powinien zostać uruchomiony, gdy aplikacja jest debugowana.

**Uruchamianie przeglądarki z adresem URL**

Wybierz tę opcję, aby określić, że określony adres URL powinien być dostępny, gdy aplikacja jest debugowana.

## <a name="start-options"></a>Opcje startu

**Argumenty wiersza polecenia**

W tym polu tekstowym wprowadź argumenty wiersza polecenia, które mają być używane do debugowania.

**Katalog roboczy**

W tym polu tekstowym wprowadź katalog, z którego zostanie uruchomiony projekt. Możesz też kliknąć przycisk Przeglądaj (**...**), aby wybrać katalog.

**Korzystanie ze zdalnego komputera**

Aby debugować aplikację z komputera zdalnego, zaznacz to pole wyboru i wprowadź ścieżkę do komputera zdalnego w polu tekstowym.

## <a name="debugger-engines"></a>Silniki debugera

**Włączanie debugowania kodu natywnego**

Ta opcja określa, czy debugowanie kodu macierzystego jest obsługiwane. Zaznacz to pole wyboru, jeśli wywołujesz obiekty COM lub jeśli uruchomisz niestandardowy program napisany w kodzie macierzystym, który wywołuje projekt i musisz debugować kod macierzysty. Wyczyść to pole wyboru, aby wyłączyć debugowanie kodu niezarządzanego. To pole wyboru jest domyślnie wyczyszczone.

**Włączanie debugowania programu SQL Server**

Zaznacz lub wyczyść to pole wyboru, aby włączyć lub wyłączyć debugowanie procedur SQL z aplikacji języka Visual Basic. To pole wyboru jest domyślnie wyczyszczone.

## <a name="see-also"></a>Zobacz też

- [Pierwsze spojrzenie na debugera](../../debugger/debugger-feature-tour.md)
- [Ustawienia projektu dla konfiguracji debugowania języka C#](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania języka Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Porady: debugowanie aplikacji ClickOnce przy użyciu ograniczonych uprawnień](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Porady: tworzenie i edycja konfiguracji](../../ide/how-to-create-and-edit-configurations.md)
