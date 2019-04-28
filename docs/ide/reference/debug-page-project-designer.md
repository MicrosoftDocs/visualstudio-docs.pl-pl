---
title: Strona debugowania, Projektant projektu
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a49b2c77833538cb983f776a2f54ad332fb87f59
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968188"
---
# <a name="debug-page-project-designer"></a>Strona debugowania, Projektant projektu

Użyj **debugowania** strony **projektanta projektu** do ustawiania właściwości do debugowania zachowania w projekcie języka Visual Basic lub C#.

Aby uzyskać dostęp do **debugowania** wybierz węzeł projektu w **Eksploratora rozwiązań**. Na **projektu** menu, wybierz  **\<nazwa_projektu > właściwości**. Podczas **projektanta projektu** zostanie wyświetlona, kliknij przycisk **debugowania** kartę.

> [!NOTE]
> W tym temacie nie ma zastosowania do aplikacji platformy uniwersalnej systemu Windows. Zobacz [rozpocząć sesję debugowania (VB, C#, C++ i XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) dla aplikacji platformy uniwersalnej systemu Windows.

## <a name="configuration-and-platform"></a>Konfiguracja i platforma

Poniższe opcje pozwalają wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.

**Konfiguracja**

Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Te ustawienia mogą mieć **debugowania** (ustawienie domyślne), **wersji**, lub **wszystkie konfiguracje**.

**Platforma**

Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Można wybierać **dowolny Procesor** (ustawienie domyślne), **x64**, i **x86**.

## <a name="start-action"></a>Akcja uruchamiania

**Akcja uruchamiania** wskazuje element uruchamianą podczas debugowania aplikacji: projekt, program niestandardowy, adres URL lub nie rób. Domyślnie ta opcja jest ustawiona na **spustit projekt**. **Akcja uruchamiania** ustawienie **debugowania** strony określa wartość `StartAction` właściwości.

**Rozpocznij projekt**

Wybierz tę opcję, aby określić, że plik wykonywalny (dla aplikacji Windows i aplikacji Konsolowej projektów) powinna być uruchamiana podczas debugowania aplikacji. Ta opcja jest domyślnie wybrana.

**Uruchom zewnętrzny program**

Wybierz tę opcję, aby określić, że określony program powinna być uruchamiana podczas debugowania aplikacji.

**Uruchom przeglądarkę z adresem URL**

Wybierz tę opcję, aby określić, czy określony adres URL jest dostępny podczas debugowania aplikacji.

## <a name="start-options"></a>Opcje uruchamiania

**Argumenty wiersza polecenia**

W tym polu tekstowym wprowadź argumenty wiersza polecenia używane do debugowania.

**Katalog roboczy**

W tym polu tekstowym wprowadź katalog, w którym projekt zostanie uruchomiony. Lub kliknij przycisk przeglądania (**...** ) można wybrać katalog.

**Użyj komputera zdalnego**

Aby debugować aplikację z komputera zdalnego, zaznacz to pole wyboru, a następnie wprowadź ścieżkę do komputera zdalnego, w polu tekstowym.

## <a name="debugger-engines"></a>Aparaty debugowania

**Włącz debugowanie kodu natywnego**

Ta opcja określa, czy obsługiwane jest debugowanie kodu natywnego. Zaznacz to pole wyboru, jeśli wywołań do obiektów COM lub uruchomić program niestandardowy napisanymi w kodzie natywnym, który odwołuje się do projektu i muszą debugowanie kodu natywnego. Wyczyść to pole wyboru, aby wyłączyć debugowanie kodu niezarządzanego. To pole wyboru jest domyślnie wyczyszczone.

**Włącz debugowanie programu SQL Server**

Zaznacz lub wyczyść to pole wyboru, aby włączyć lub wyłączyć debugowanie procedur SQL z aplikacji Visual Basic. To pole wyboru jest domyślnie wyczyszczone.

## <a name="see-also"></a>Zobacz także

- [Pierwsze spojrzenie na debugera](../../debugger/debugger-feature-tour.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C#](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Instrukcje: Debugowanie aplikacji ClickOnce przy użyciu ograniczonych uprawnień](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Instrukcje: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md)