---
title: 'Instrukcje: debugowanie częściowej aplikacji zaufania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], partial trust applications
- partial trust applications
- security [Visual Studio], partial trust applications
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 030fef750cc1e0f0932de32fca1a0ffef56bc8f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704490"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Porady: debugowanie częściowo zaufanych aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemu Windows i aplikacji konsolowych.  
  
 [Zabezpieczenia i wdrożenie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md) ułatwiają wdrażanie aplikacji częściowo zaufanych, które wykorzystują [zabezpieczenia dostępu kodu](https://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) , aby ograniczyć dostęp do zasobów na komputerze.  
  
 Debugowanie aplikacji częściowo zaufanej może być wyzwaniem, ponieważ częściowo zaufane aplikacje mają różne uprawnienia zabezpieczeń (i w związku z tym zachowują się inaczej) w zależności od tego, gdzie są zainstalowane. Jeśli program jest instalowany z Internetu, częściowo zaufana aplikacja będzie miała kilka uprawnień. Jeśli program jest instalowany z lokalnego intranetu, będzie miał więcej uprawnień i w przypadku instalacji z komputera lokalnego będzie miał pełne uprawnienia. Mogą również istnieć strefy niestandardowe z uprawnieniami niestandardowymi. Może być konieczne debugowanie częściowej aplikacji zaufania w ramach dowolnego lub wszystkich tych warunków. Na szczęście program Visual Studio również ułatwia.  
  
 Przed rozpoczęciem sesji debugowania w programie Visual Studio można wybrać strefę, z której ma zostać zasymulowana aplikacja. Po rozpoczęciu debugowania aplikacja będzie mieć uprawnienia odpowiednie dla aplikacji częściowo zaufanej zainstalowanej z tej strefy. Dzięki temu można zobaczyć zachowanie aplikacji w taki sposób, aby była widoczna dla użytkownika, który pobrał go z tej strefy.  
  
 Jeśli aplikacja próbuje wykonać akcję, do której nie ma uprawnień, wystąpi wyjątek. W tym momencie Asystent wyjątków umożliwia dodanie dodatkowych uprawnień, co umożliwia ponowne uruchomienie sesji debugowania z odpowiednimi uprawnieniami w celu uniknięcia problemu.  
  
 Później można wrócić i zobaczyć, które uprawnienia zostały dodane podczas debugowania. Jeśli użytkownik musiał dodać uprawnienie podczas debugowania, prawdopodobnie wskazuje, że musisz dodać monit o zgodę użytkownika w tym momencie w kodzie.  
  
> [!NOTE]
> Wizualizatory debugera wymagają większych uprawnień niż jest to dozwolone w przypadku aplikacji częściowo zaufanej. Wizualizatory nie będą ładowane po zatrzymaniu w kodzie z częściowym zaufaniem. Aby debugować przy użyciu wizualizatora, należy uruchomić kod z pełnym zaufaniem.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>Aby wybrać strefę dla aplikacji częściowej zaufania  
  
1. W menu **projekt** wybierz polecenie właściwości _ProjectName_**Properties**.  
  
2. Na stronach właściwości *ProjectName* kliknij stronę **zabezpieczenia** .  
  
3. Wybierz pozycję **Włącz ustawienia zabezpieczeń ClickOnce**.  
  
4. W obszarze **strefa, z której zostanie zainstalowana aplikacja**, kliknij listę rozwijaną i wybierz strefę, z której ma zostać zasymulowana instalacja aplikacji.  
  
     **Uprawnienia wymagane przez** siatkę aplikacji pokazują wszystkie dostępne uprawnienia. Znacznik wyboru oznacza uprawnienia przyznane aplikacji.  
  
5. Jeśli wybrana strefa była **(niestandardowa)**, wybierz odpowiednie ustawienia niestandardowe w kolumnie **Ustawienia** w siatce **uprawnienia** .  
  
6. Kliknij przycisk **OK** , aby zamknąć strony właściwości.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>Aby dodać dodatkowe uprawnienie w przypadku wystąpienia wyjątku zabezpieczeń  
  
1. Zostanie wyświetlone okno dialogowe **Asystent wyjątków** z komunikatem: **SecurityException nie został obsłużony.**  
  
2. W oknie dialogowym **Asystent wyjątków** w obszarze **Akcje**kliknij pozycję **Dodaj uprawnienie do projektu**.  
  
3. Zostanie wyświetlone okno dialogowe **Ponowne uruchamianie debugowania** .  
  
    - Jeśli chcesz ponownie uruchomić sesję debugowania z nowym uprawnieniem, kliknij przycisk **tak**.  
  
    - Jeśli nie chcesz jeszcze uruchamiać ponownie, kliknij przycisk **nie**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>Aby wyświetlić dodatkowe uprawnienia dodane podczas debugowania  
  
1. W menu **projekt** wybierz polecenie właściwości _ProjectName_**Properties**.  
  
2. Na stronach właściwości *ProjectName* kliknij stronę **zabezpieczenia** .  
  
3. Sprawdź **uprawnienia wymagane przez** siatkę aplikacji. Wszelkie dodane dodatkowe uprawnienia mają dwie ikony w **dołączonej** kolumnie: normalny znacznik wyboru, który ma wszystkie dołączone uprawnienia, oraz dodatkową ikonę, która wygląda jak dymek zawierający literę "i".  
  
4. Użyj pionowego paska przewijania, aby wyświetlić wszystkie **uprawnienia wymagane przez** siatkę aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)
