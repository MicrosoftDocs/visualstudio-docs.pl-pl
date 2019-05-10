---
title: 'Błąd: Udostępnianie plików Windows skonfigurowano... | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c45a1b74-61ec-4c64-9e2c-13051a4f50a5
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96d65ae615522bcee43ddf5e8181e96eecc0d958
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040860"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Błąd: Udostępnianie plików systemu Windows zostało skonfigurowane...
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Udostępnianie plików Windows został skonfigurowany, tak aby połączy się z komputerem zdalnym przy użyciu innej nazwy użytkownika. Jest to niezgodne z funkcją debugowania zdalnego  
  
 Bieżący plik Konfiguracja udostępniania jest skonfigurowany do łączenia się z komputerem zdalnym przy użyciu innej nazwy użytkownika. Zdalne debugowanie nie jest możliwe, w tym scenariuszu.  
  
 Aby rozwiązać ten problem, zaloguj się na komputerze przy użyciu nazwy konta lub zmienić udostępniania plików do używania nazwy konta, który debugujesz w obszarze.  
  
 Jeśli chcesz się połączyć z komputerem zdalnym przy użyciu tej nazwy użytkownika, musisz najpierw odłączyć z komputera zdalnego.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zaloguj się na komputerze lokalnym komputera, który debugujesz, przy użyciu nazwy konta.  
  
     —lub—  
  
     . Rozłącz z komputera zdalnego, a następnie ponownie skonfiguruj Udostępnianie plików, połączyć się z innego komputera przy użyciu nazwy konta:  
  
    1. Na **Start** menu wskaż **Akcesoria**, a następnie kliknij przycisk **polecenia**.  
  
    2. W wierszu polecenia Windows wpisz:  
  
         `net use /delete computer_name`  
  
    3. Zmień ustawienia udostępniania plików przy użyciu dowolnej z metod opisanych w Pomocy Windows.
