---
title: Okno dialogowe Edytuj i Kontynuuj komunikat o błędzie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5437ef982309ef8595f08283f2685e93d346e764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428301"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Komunikat o błędzie Edytuj i kontynuuj — Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To okno dialogowe jest wyświetlane w przypadku debugowania w języku, który obsługuje funkcję Edytuj i Kontynuuj, ale opcja **Edytuj i Kontynuuj** nie jest dostępna dla typu wprowadzonych zmian kodu. Komunikat o błędzie wewnątrz pola zawiera bardziej szczegółowy opis. Możliwe przyczyny wyświetlenia tego okna dialogowego obejmują:  
  
- Podjęto próbę edytowania kodu zarządzanego, gdy włączono debugowanie niezarządzane. Tryb Edytuj i Kontynuuj nie działa w przypadku debugowania w trybie mieszanym.  
  
- Podjęto próbę edycji kodu SQL Server.  
  
- Podjęto próbę edycji kodu podczas debugowania zrzutu Dr. Watson.  
  
- Podjęto próbę edycji kodu po wystąpieniu nieobsługiwanego wyjątku i wybraniu opcji "**odwinięcie stosu wywołań w przypadku nieobsługiwanych wyjątków**".  
  
- Podjęto próbę edycji kodu podczas debugowania osadzonej aplikacji środowiska uruchomieniowego.  
  
- Podjęto próbę edycji kodu w programie, który został dołączony do programu zamiast z menu **Debuguj** .  
  
- Podjęto próbę edycji zoptymalizowanego kodu.  
  
- Podjęto próbę edytowania kodu zarządzanego, gdy element docelowy jest aplikacją 64-bitową. Jeśli chcesz użyć opcji Edytuj i Kontynuuj, musisz ustawić wartość docelową na x86. (*Project* **Właściwości**projektu, karta **kompilacja** , **Zaawansowane ustawienie kompilatora** ).  
  
- Próbowano edytować kod w zestawie, który został zmodyfikowany podczas debugowania i został ponownie załadowany.  
  
- Próbowano edytować kod w zestawie, który nie został załadowany.  
  
- Rozpoczęto debugowanie starej wersji aplikacji (ponieważ nowa wersja ma błędy kompilacji).  
  
- Podjęto próbę edytowania kodu podczas jego działania.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **OK**  
 Zamknij okno dialogowe i Anuluj poprzednią próbę edycji.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługiwane zmiany kodu (C++)](../debugger/supported-code-changes-cpp.md)
