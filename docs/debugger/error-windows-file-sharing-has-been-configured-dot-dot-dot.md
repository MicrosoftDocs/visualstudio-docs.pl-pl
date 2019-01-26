---
title: 'Błąd: Udostępnianie plików Windows skonfigurowano... | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 257d7a0ce597cc8cbbadca975ee3db60d4e3adcc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951849"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Błąd: Udostępnianie plików systemu Windows zostało skonfigurowane...
Udostępnianie plików Windows został skonfigurowany, tak aby połączy się z komputerem zdalnym przy użyciu innej nazwy użytkownika. Jest to niezgodne z funkcją debugowania zdalnego  
  
 Bieżący plik Konfiguracja udostępniania jest skonfigurowany do łączenia się z komputerem zdalnym przy użyciu innej nazwy użytkownika. Zdalne debugowanie nie jest możliwe, w tym scenariuszu.  
  
 Aby rozwiązać ten problem, zaloguj się na komputerze przy użyciu nazwy konta lub zmienić udostępniania plików do używania nazwy konta, który debugujesz w obszarze.  
  
 Jeśli chcesz się połączyć z komputerem zdalnym przy użyciu tej nazwy użytkownika, musisz najpierw odłączyć z komputera zdalnego.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zaloguj się na komputerze lokalnym komputera, który debugujesz, przy użyciu nazwy konta.  
  
     —lub—  
  
     . Rozłącz z komputera zdalnego, a następnie ponownie skonfiguruj Udostępnianie plików, połączyć się z innego komputera przy użyciu nazwy konta:  
  
    1.  Na **Start** menu wskaż **Akcesoria**, a następnie kliknij przycisk **polecenia**.  
  
    2.  W wierszu polecenia Windows wpisz:  
  
         `net use /delete computer_name`  
  
    3.  Zmień ustawienia udostępniania plików przy użyciu dowolnej z metod opisanych w Pomocy Windows.