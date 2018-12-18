---
title: 'Błąd: Nie masz uprawnień do sprawdzania proces&#39;tożsamości s | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f37cf6f6a1a72435b549942fa03d821c900718a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472035"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Błąd: Nie masz uprawnień do sprawdzania proces&#39;tożsamości s
Nie masz uprawnień umożliwiających sprawdzenie tożsamości procesu. Może to być spowodowane konfiguracji systemu.  
  
 Debuger nie mógł sprawdzić tożsamość procesu, który jest niezbędne informacje dotyczące debugowania. Najbardziej prawdopodobną przyczyną jest wyłączana usług terminalowych. Usługi terminalowe jest domyślnie włączona. Wykonaj następujące kroki, aby włączyć je ponownie.  
  
### <a name="to-enable-terminal-services"></a>Aby włączyć usługi terminalowe  
  
1.  Kliknij przycisk **Start** , a następnie wybierz **Panelu sterowania**.  
  
2.  W Panelu sterowania, wybierz **Przełącz do widoku klasycznego**, jeśli to konieczne, a następnie kliknij dwukrotnie **narzędzia administracyjne**.  
  
3.  W **narzędzia administracyjne** okna, kliknij dwukrotnie **Zarządzanie komputerem**.  
  
4.  W oknie Zarządzanie komputerem rozwiń węzeł **usługi i aplikacje** węzła.  
  
5.  W obszarze **usługi i aplikacje**, kliknij przycisk **usług**.  
  
     W okienku po prawej stronie zostanie wyświetlona lista usług.  
  
6.  W **usług** listy, kliknij prawym przyciskiem myszy **usług terminalowych** , a następnie wybierz **właściwości**.  
  
7.  W **właściwości usług terminalowych** okna, przejdź do **ogólne** kartę i ustawić **uruchamiana** do **ręcznego**.  
  
8.  Kliknij przycisk **OK**.  
  
9. Uruchom ponownie komputer.  
  
     Ta procedura nie automatycznie włączyć pulpitu zdalnego. Jeśli chcesz włączyć Pulpit zdalny na komputerze, należy wykonać poniższą procedurę dodatkowe.  
  
### <a name="to-enable-remote-desktop"></a>Aby włączyć Pulpit zdalny  
  
1.  Kliknij przycisk **Start** , a następnie kliknij prawym przyciskiem myszy **Mój komputer**.  
  
2.  Wybierz **właściwości**.  
  
     **Właściwości systemu** okno jest wyświetlane.  
  
3.  Kliknij przycisk **zdalnego**.  
  
4.  W obszarze **pulpitu zdalnego**, wybierz pozycję **umożliwiają użytkownikom zdalne łączenie się na tym komputerze**.  
  
5.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)