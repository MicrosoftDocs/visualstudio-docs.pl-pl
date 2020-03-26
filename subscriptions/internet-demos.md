---
title: Używanie kluczy produktu do obsługi pokazów internetowych za pośrednictwem usług terminalowych | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 1c5ede60-cb5a-4d5f-a6a2-a1f536f6c4ad
ms.date: 03/09/2020
ms.topic: conceptual
description: Dowiedz się, jak używać kluczy produktów do obsługi pokazów internetowych za pośrednictwem usług terminalowych i włączania dostępu RDS
ms.openlocfilehash: 2d5f23f0d161ee9f50569e0ff7f8ce585c8c49ff
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232439"
---
# <a name="internet-demonstrations-via-terminal-services"></a>Pokazy internetowe za pośrednictwem usług terminalowych
W przypadku subskrypcji programu Visual Studio użytkownicy końcowi mogą zapewniać użytkownikom końcowym dostęp do pokazów internetowych programów za pośrednictwem usług terminalowych (Windows Server 2003 lub Windows Server 2008) lub usług pulpitu zdalnego (Windows Server 2008 R2 i nowszych). W ten sposób może jednocześnie uzyskać dostęp do demonstracji do 200 anonimowych użytkowników. Demonstracja nie może używać danych produkcyjnych. Subskrybenci programu Visual Studio mają licencję na demonstrować swoje aplikacje użytkownikom końcowym. Ta demonstracja internetowa przy użyciu usług terminalowych (TS) lub usług pulpitu zdalnego (RDS) jest jedynym scenariuszem, w którym użytkownicy końcowi bez subskrypcji programu Visual Studio mogą wchodzić w interakcje z aplikacją demonstracyjną, gdy oprogramowanie jest licencjonowane za pośrednictwem programu Visual Subskrypcje studyjne.

Jest to dodatek do praw deweloperskich/testowych, gdzie subskrybenci programu Visual Studio mogą używać dowolną liczbę połączeń rds lub usług TS, ile potrzeba.

## <a name="enabling-rds-access"></a>Włączanie dostępu rds
Subskrybenci programu Visual Studio mogą zwiększyć liczbę użytkowników, którzy mogą uzyskiwać dostęp do systemu Windows Server za pośrednictwem usługi RDS, wprowadzając klucz produktu podany na karcie [Klucze produktu](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) w [portalu subskrybenta](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Aby uzyskać klucz produktu, połącz się ze stroną Klucze produktu i przewiń w dół do wersji uruchomionego systemu Windows Server. Znajdź pozycję "Windows Server < version > R2 Remote Desktop Services < połączenia > użytkownika lub urządzenia" i kliknij łącze **Klucz oświadczeń.** Jeśli na przykład usługi RDS są używane w systemie Windows Server 2012 R2, a wdrożenie jest używane przy użyciu licencji CAL użytkowników, wybierz opcję "Połączenia użytkowników usług pulpitu zdalnego systemu Windows Server 2012 (50)".
Dla systemu Windows Server 2008 R2 dostępnych jest pięć kluczy każdego typu, a każdy klucz obsługuje 20 połączeń. W systemie Windows Server 2012 R2 dostępne są cztery klucze dla każdego typu, które obsługują po 50 połączeń.

## <a name="to-enable-additional-connections-in-windows-server"></a>Aby włączyć dodatkowe połączenia w systemie Windows Server:
1. Otwórz Menedżera serwera.
2. Otwórz listę Serwery w lewym okienku nawigacyjnym.
3. Kliknij prawym przyciskiem myszy na serwerze licencji i wybierz "Zainstaluj licencje".
4. Postępuj zgodnie z krokami w kreatorze.  Wybierając typ umowy, wybierz opcję "Pakiet licencji (handel detaliczny)" i wprowadź klucz produktu uzyskany z portalu MY.

Użytkownicy końcowi mogą łączyć się z aplikacjami dostępu za pośrednictwem usług RDS, jeśli spełnione są następujące warunki:
- Użytkownicy muszą być anonimowi (w stanie nieue uwierzytelnionym).
- Połączenia muszą być nawiązywki przez Internet.
- Do 200 równoczesnych połączeń użytkownika mogą być używane do demonstracji aplikacji.
- Klucze produktu, aby włączyć połączenia użytkownika muszą być uzyskane przez subskrybenta programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Documenation systemu Windows Server](https://docs.microsoft.com/windows-server/)
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Jeśli potrzebujesz wskazówek dotyczących wdrażania usług pulpitu zdalnego, zapoznaj się z wieloczęściową serią blogów dotyczących **wdrażania sesji usług pulpitu zdalnego (RDS) 2012** w programie https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerf. 

Jeśli masz jakieś pytania, odwiedź [forum usług pulpitu zdalnego firmy Microsoft](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS).
