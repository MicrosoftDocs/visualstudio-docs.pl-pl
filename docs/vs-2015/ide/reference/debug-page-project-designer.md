---
title: Strona debugowania, Projektant projektu | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 22a1accc7421e169ee345fda0446a8474d2eda00
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776147"
---
# <a name="debug-page-project-designer"></a>Strona debugowania, Projektant projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
> [!WARNING]
>  Ten temat nie dotyczy aplikacji Windows Store. Zobacz [uruchomić sesję debugowania (VB, C#, C++ i XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) w Centrum deweloperów Windows.  
  
 Użyj **debugowania** strony **projektanta projektu** do ustawiania właściwości do debugowania zachowania w projekcie języka Visual Basic lub C#.  
  
 Aby uzyskać dostęp do **debugowania** wybierz węzeł projektu w **Eksploratora rozwiązań**. Na **projektu** menu, wybierz _ProjectName_**właściwości**. Podczas **projektanta projektu** zostanie wyświetlona, kliknij przycisk **debugowania** kartę.  
  
## <a name="configuration-and-platform"></a>Konfiguracja i platforma  
 Poniższe opcje pozwalają wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.  
  
 **Konfiguracja**  
 Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Te ustawienia mogą mieć **debugowania** (ustawienie domyślne), **wersji**, lub **wszystkie konfiguracje**. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
 **Platforma**  
 Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Można wybierać **dowolny Procesor** (ustawienie domyślne), **x64**, i **x86**. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
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
  
## <a name="enable-debuggers"></a>Włączyć debugery  
 **Włącz debugowanie kodu niezarządzanego**  
 Ta opcja określa, czy obsługiwane jest debugowanie kodu natywnego. Zaznacz to pole wyboru, jeśli wywołań do obiektów COM lub uruchomić program niestandardowy napisanymi w kodzie natywnym, który odwołuje się do projektu i muszą debugowanie kodu natywnego. Wyczyść to pole wyboru, aby wyłączyć debugowanie kodu niezarządzanego. To pole wyboru jest domyślnie wyczyszczone.  
  
 **Włącz debugowanie programu SQL Server**  
 Zaznacz lub wyczyść to pole wyboru, aby włączyć lub wyłączyć debugowanie procedur SQL z aplikacji Visual Basic. To pole wyboru jest domyślnie wyczyszczone.  
  
 **Włącz procesu hostingu Visual Studio**  
 Zaznacz to pole wyboru, aby włączyć procesu hostingu Visual Studio. To pole wyboru jest zaznaczone domyślnie. Aby uzyskać więcej informacji, zobacz [proces hostingu (vshost.exe)](../../ide/hosting-process-vshost-exe.md).  
  
 Aby debugować w strefie zabezpieczeń, należy włączyć tę opcję i **Debuguj aplikację z wybranym zestawem uprawnień** w [okno dialogowe Zaawansowane ustawienia zabezpieczeń](../../ide/reference/advanced-security-settings-dialog-box.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Ustawienia projektu dla języka C# konfiguracji debugowania](../../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla języka Visual Basic konfiguracji debugowania](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Zarządzanie, debugowanie — właściwości](http://msdn.microsoft.com/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)   
 [Instrukcje: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Instrukcje: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md)
