---
title: 'Instrukcje: debugowanie pliku wykonywalnego, który nie jest częścią rozwiązania programu Visual Studio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e33233fd313cd6a73013ce55333a860663ddb601
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704521"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>Porady: debugowanie pliku wykonywalnego, który nie jest częścią rozwiązania programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czasami może być konieczne debugowanie pliku wykonywalnego, który nie jest częścią [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Może to być plik wykonywalny utworzony poza programem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub plik wykonywalny otrzymany od innego użytkownika.  
  
 Zwykłą odpowiedzią na ten problem jest uruchomienie pliku wykonywalnego poza programem Visual Studio i dołączenie go do niego przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugera. Aby uzyskać więcej informacji, zobacz[dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Dołączenie do aplikacji wymaga wykonania kilku czynności ręcznych, więc zajmie to kilka sekund. To małe opóźnienie oznacza, że dołączanie nie będzie pomocne w przypadku próby debugowania problemu występującego podczas uruchamiania. Ponadto, jeśli debugujesz program, który nie czeka na dane wejściowe użytkownika i zakończy się szybko, możesz nie mieć czasu na dołączenie do niego. Jeśli [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] zainstalowano program, można utworzyć projekt exe dla takiego programu.  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Aby utworzyć projekt EXE dla istniejącego pliku wykonywalnego  
  
1. W menu **plik** kliknij polecenie **Otwórz** i wybierz pozycję **projekt**.  
  
2. W oknie dialogowym **Otwórz projekt** kliknij listę rozwijaną obok pola **Nazwa pliku** , a następnie wybierz pozycję **wszystkie pliki projektu**.  
  
3. Znajdź plik wykonywalny i kliknij przycisk **OK**.  
  
     Spowoduje to utworzenie tymczasowego rozwiązania zawierającego plik wykonywalny.  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Aby zaimportować plik wykonywalny do rozwiązania programu Visual Studio  
  
1. W menu **plik** wskaż polecenie **Dodaj projekt**, a następnie kliknij pozycję **istniejący projekt**.  
  
2. W oknie dialogowym **Dodaj istniejący projekt** kliknij listę rozwijaną obok pola **Nazwa pliku** , a następnie wybierz pozycję **wszystkie pliki projektu**.  
  
3. Znajdź i wybierz plik wykonywalny.  
  
4. Kliknij przycisk **OK**.  
  
5. Uruchom plik wykonywalny, wybierając polecenie wykonywania, takie jak **Start**, z menu **Debuguj** .  
  
    > [!NOTE]
    > Nie wszystkie języki programowania obsługują projekty EXE. Zainstaluj [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , jeśli musisz użyć tej funkcji.  
  
     Podczas debugowania pliku wykonywalnego bez kodu źródłowego dostępne funkcje debugowania są ograniczone, niezależnie od tego, czy dołączysz do uruchomionego pliku wykonywalnego, czy dodajesz plik wykonywalny do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania. Jeśli plik wykonywalny został skompilowany bez informacji debugowania w formacie zgodnym, dostępne funkcje są dodatkowo ograniczone. Jeśli masz kod źródłowy, najlepszym rozwiązaniem jest zaimportowanie kodu źródłowego do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i utworzenie kompilacji debugowania pliku wykonywalnego w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [DBG, pliki](https://msdn.microsoft.com/91e449e9-8b65-4123-960f-2107cd1f1cfd)
