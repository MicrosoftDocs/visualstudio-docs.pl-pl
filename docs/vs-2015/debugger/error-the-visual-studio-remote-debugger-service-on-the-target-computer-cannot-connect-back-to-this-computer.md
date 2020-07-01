---
title: 'Błąd: usługa zdalny debuger programu Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 80a7de83f118b38d9a3c71f1c7e7febf48e0f5bc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520513"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Błąd: Usługa zdalnego debugera Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten błąd oznacza, że usługa zdalny debuger programu Visual Studio jest uruchomiona w ramach konta użytkownika, którego nie można uwierzytelnić, gdy próbuje nawiązać połączenie z komputerem, na którym przeprowadzasz debugowanie.  
  
 W poniższej tabeli przedstawiono, jakie konta mogą uzyskać dostęp do komputera:  
  
|Scenariusz|Konto LocalSystem|Konto domeny|Konta lokalne, które mają taką samą nazwę użytkownika i hasło na obu komputerach|  
|-|-|-|-|-|  
|Oba komputery w tej samej domenie|Tak|Tak|Tak|  
|Oba komputery w domenach z zaufaniem dwukierunkowym|Nie|Nie|Yes|  
|Jeden lub oba komputery w grupie roboczej|Nie|Nie|Yes|  
|Komputery w różnych domenach|Nie|Nie|Yes|  
  
 Ponadto:  
  
- Konto, na którym uruchomiono usługę zdalny debuger programu Visual Studio, powinno być kontem administratora na komputerze zdalnym, aby można było debugować każdy proces.  
  
- Konto musi mieć również przyznane `Log on as a service` uprawnienie na komputerze zdalnym korzystającym z narzędzia administracyjnego **zasad zabezpieczeń lokalnych** .  
  
- Jeśli używasz konta lokalnego dostępu do komputera, musisz uruchomić usługę zdalny debuger programu Visual Studio w ramach konta lokalnego.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Upewnij się, że usługa zdalny debuger programu Visual Studio została prawidłowo skonfigurowana na komputerze zdalnym. Aby uzyskać więcej informacji, zobacz [Konfigurowanie narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
2. Uruchom usługę zdalnego debugera w ramach konta, które ma dostęp do komputera hosta debugera, jak pokazano w poprzedniej tabeli.  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>Aby dodać uprawnienie "Logowanie w trybie usługi"  
  
1. W menu **Start** wybierz pozycję **Panel sterowania**.  
  
2. W panelu sterowania wybierz pozycję **Widok klasyczny**, w razie potrzeby.  
  
3. Kliknij dwukrotnie pozycję **Narzędzia administracyjne**.  
  
4. W oknie Narzędzia administracyjne kliknij dwukrotnie pozycję **zasady zabezpieczeń lokalnych**.  
  
5. W oknie **Ustawienia zabezpieczeń lokalnych** rozwiń folder **Zasady lokalne** .  
  
6. Kliknij pozycję **Przypisywanie praw użytkownika**.  
  
7. W kolumnie **zasady** kliknij dwukrotnie pozycję **Logowanie jako usługa** , aby wyświetlić bieżące przypisania lokalnego zasady grupy w oknie dialogowym **Logowanie jako usługa** .  
  
8. Aby dodać nowych użytkowników, kliknij przycisk **Dodaj użytkownika lub grupę** .  
  
9. Po zakończeniu dodawania użytkowników kliknij przycisk **OK**.  
  
### <a name="to-work-around-this-error"></a>Aby obejść ten błąd  
  
- Uruchom Monitor zdalnego debugowania jako aplikację zamiast usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)
