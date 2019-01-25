---
title: Zaufanie rozwiązań pakietu Office przy użyciu list dołączania
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2b0e3df3562fe9a7bcbf2ca9cdc899b9303eb19a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868618"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Zaufanie rozwiązań pakietu Office przy użyciu list dołączania
  Włączenie listy umożliwiają użytkownikom udzielenia zaufania do rozwiązań pakietu Office, które są podpisane za pomocą certyfikatu, który identyfikuje wydawcy. Listy dołączania są specyficzne dla użytkownika i może służyć do dostosowywania na poziomie dokumentu i dodatków narzędzi VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Gdy użytkownik uruchamia rozwiązań pakietu Office, które nie zostały nadane dla relacji zaufania dla danego użytkownika, rozwiązania Microsoft Office jej wyświetla monit o podanie decyzja dotycząca zabezpieczeń za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] monit o udzielenie zaufania. Jeśli użytkownik zdecyduje się na rozwiązaniu zaufania, przebiegów dostosowywania i użytkownik nie jest monitowany przy następnym.  
  
## <a name="inclusion-list-and-windows-installer"></a>Lista dołączania i Instalator Windows  
 Instalowanie rozwiązania dla pakietu Office do *Program Files* katalogu przy użyciu Instalatora Windows wymaga uprawnień administratora. Dla rozwiązań pakietu Office w *Program Files* katalogu, ponieważ rozwiązań pakietu Office zostały już przyznane uprawnienie FullTrust Visual Studio Tools for Office runtime nie jest już sprawdza lista dołączania.  
  
## <a name="clickonce-trust-prompt"></a>Monit o udzielenie zaufania ClickOnce  
 Za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] wdrożenia dla rozwiązań pakietu Office, Administratorzy można skonfigurować poziom monitu zaufania do Zezwalaj na monit, wyłącz monitowanie lub wymagają zaufanego certyfikatu. Ta konfiguracja jest implementowana przy użyciu klucza rejestru, który kontroluje dostęp do listy dołączania.  
  
 Jeśli monit zostanie wyłączona, można zainstalować tylko w przypadku rozwiązań, które mają certyfikat zaufanego i znanego. Jeśli poziom monitem jest ustawiony na wymagane Authenticode, rozwiązania muszą być podpisane przy użyciu certyfikatu ze znanego urzędu, ale nie wymaga certyfikatu, który tworzy łańcuch zaufanego głównego urzędu certyfikacji (zaufanego certyfikatu). Jeśli dozwolone jest monitowanie, rozwiązanie może być podpisany przy użyciu certyfikatu przy użyciu tożsamości nieznany. W tym scenariuszu decyzji zaufania jest odroczone do użytkownika końcowego, a tymczasowy certyfikat będzie odpowiednia do zainstalowania rozwiązania.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie zabezpieczeń listy dołączania](../vsto/how-to-configure-inclusion-list-security.md) i tabela 2, zatytułowany monitowania poziom rejestru klucz wartość Uruchom skutki, [ClickOnce Konfigurowanie zaufanych wydawców](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="structure-of-the-inclusion-list"></a>Struktura tej listy dołączania  
 Wpis na liście prawidłowe dołączania ma dwie części: ścieżka do pliku manifestu wdrożenia, a klucz publiczny służący do podpisania rozwiązania. Po dodaniu rozwiązania do listy dołączania jest uznawane za zaufane. Po uruchomieniu rozwiązania dla pakietu Office aplikacji pakietu Office porównuje klucz publiczny na liście dołączania przy użyciu klucza podpisywania w pliku manifestu wdrożenia, aby sprawdzić, czy rozwiązanie, które jest aktualnie uruchomione jest taka sama co wersja oryginalna zaufanych.  
  
## <a name="see-also"></a>Zobacz także  
 [Udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)  
