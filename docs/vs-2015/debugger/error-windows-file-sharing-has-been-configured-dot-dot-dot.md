---
title: 'Błąd: udostępnianie plików systemu Windows zostało skonfigurowane... | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157500"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Błąd: Udostępnianie plików systemu Windows zostało skonfigurowano...
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Udostępnianie plików systemu Windows zostało skonfigurowane w taki sposób, aby nawiązać połączenie z komputerem zdalnym przy użyciu innej nazwy użytkownika. Jest to niezgodne z debugowaniem zdalnym  
  
 Bieżąca konfiguracja udostępniania plików jest skonfigurowana do nawiązywania połączenia z komputerem zdalnym przy użyciu innej nazwy użytkownika. Debugowanie zdalne nie jest możliwe w tym scenariuszu.  
  
 Aby naprawić ten błąd, zaloguj się na komputerze przy użyciu innej nazwy konta lub Zmień udostępnianie plików, tak aby używało nazwy konta, które jest debugowane.  
  
 Jeśli chcesz nawiązać połączenie z komputerem zdalnym przy użyciu tej nazwy użytkownika, musisz najpierw odłączyć się od komputera zdalnego.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zaloguj się na komputerze lokalnym, z którego chcesz debugować, używając innej nazwy konta.  
  
     —lub—  
  
     . Odłącz od komputera zdalnego, a następnie skonfiguruj ponownie udostępnianie plików, aby połączyć się z inną maszyną przy użyciu nazwy konta:  
  
    1. W menu **Start** wskaż polecenie **akcesoria**, a następnie kliknij pozycję **wiersz polecenia**.  
  
    2. W wierszu polecenia systemu Windows wpisz:  
  
         `net use /delete computer_name`  
  
    3. Zmień ustawienia udostępniania plików przy użyciu dowolnej metody udokumentowanej w pomocy systemu Windows.
