---
title: 'Błąd: Nie masz uprawnień do sprawdzania procesu&#39;tożsamości s | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 6233d060-85b8-42be-ae5f-bde7e1d0f241
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f173be87987cbc8bcfb3390dfdaaf5eab7501bb6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776216"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Błąd: Nie masz uprawnień do sprawdzania procesu&#39;tożsamości s
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nie masz uprawnień do sprawdzania tożsamości procesu. Może to być spowodowane konfiguracji systemu.  
  
 Debuger nie mógł sprawdzić tożsamość procesu, który jest niezbędne informacje dotyczące debugowania. Najbardziej prawdopodobną przyczyną jest usług terminalowych, które są wyłączone. Usługa terminalowa usług jest domyślnie włączone. Wykonaj następujące kroki, aby włączyć ją ponownie.  
  
### <a name="to-enable-terminal-services"></a>Aby włączyć usługi terminalowe  
  
1.  Kliknij przycisk **Start** , a następnie wybierz **Panelu sterowania**.  
  
2.  W Panelu sterowania wybierz **Przełącz na widok klasyczny**, jeśli to konieczne, a następnie kliknij dwukrotnie **narzędzia administracyjne**.  
  
3.  W **narzędzia administracyjne** okna, kliknij dwukrotnie **Zarządzanie komputerem**.  
  
4.  W oknie Zarządzanie komputerem rozwiń **usługi i aplikacje** węzła.  
  
5.  W obszarze **usługi i aplikacje**, kliknij przycisk **usług**.  
  
     W okienku po prawej stronie zostanie wyświetlona lista usług.  
  
6.  W **usług** listy, kliknij prawym przyciskiem myszy **usług terminalowych** , a następnie wybierz **właściwości**.  
  
7.  W **właściwości usług terminalowych** okna, przejdź do **ogólne** kartę i ustawić **uruchamiana** do **ręczne**.  
  
8.  Kliknij przycisk **OK**.  
  
9. Uruchom ponownie komputer.  
  
     Ta procedura nie włącza automatycznie pulpitu zdalnego. Jeśli chcesz włączyć Pulpit zdalny na komputerze, należy wykonać poniższą procedurę dodatkowe.  
  
### <a name="to-enable-remote-desktop"></a>Aby włączyć Pulpit zdalny  
  
1.  Kliknij przycisk **Start** i kliknij prawym przyciskiem myszy **Mój komputer**.  
  
2.  Wybierz **właściwości**.  
  
     **Właściwości systemu** zostanie wyświetlone okno.  
  
3.  Kliknij przycisk **zdalnego**.  
  
4.  W obszarze **pulpitu zdalnego**, wybierz opcję **umożliwiają użytkownikom zdalne łączenie się na tym komputerze**.  
  
5.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
