---
title: Ufanie rozwiązaniom pakietu Office przy użyciu list dołączania
description: Dowiedz się, jak listy dołączania umożliwiają użytkownikom udzielanie zaufania do rozwiązań pakietu Office, które są podpisane przy użyciu certyfikatu, który identyfikuje wydawcę.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9a084ad152f178b4dd03e986eb06718b0fb47c98
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968817"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Ufanie rozwiązaniom pakietu Office przy użyciu list dołączania
  Listy dołączania umożliwiają użytkownikom udzielanie zaufania do rozwiązań pakietu Office, które są podpisane przy użyciu certyfikatu, który identyfikuje wydawcę. Listy dołączania są specyficzne dla użytkownika i mogą być używane w przypadku dostosowań na poziomie dokumentu i dodatków narzędzi VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Gdy użytkownik uruchamia rozwiązanie pakietu Office, które nie uzyskało zaufania dla tego użytkownika, Microsoft Office rozwiązanie monituje go o podjęcie decyzji o zabezpieczeniach z [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] monitem o zaufaniem. Jeśli użytkownik zdecyduje się na zaufać rozwiązaniu, to dostosowanie zostanie uruchomione, a użytkownik nie będzie monitowany następnym razem.

## <a name="inclusion-list-and-windows-installer"></a>Lista dołączania i Instalator Windows
 Instalowanie rozwiązań pakietu Office w katalogu *Program Files* przy użyciu Instalator Windows wymaga uprawnień administratora. W przypadku rozwiązań pakietu Office w katalogu *Program Files* , Visual Studio Tools dla środowiska uruchomieniowego pakietu Office nie sprawdza już listy dołączania, ponieważ rozwiązania pakietu Office mają już przyznane uprawnienia FullTrust.

## <a name="clickonce-trust-prompt"></a>Monit zaufania ClickOnce
 Korzystając z [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] implementacji rozwiązań pakietu Office, Administratorzy mogą skonfigurować poziom monitu zaufania, aby zezwolić na monitowanie, wyłączyć monitowanie lub wymagać certyfikatu zaufanego. Ta konfiguracja odbywa się przy użyciu klucza rejestru, który kontroluje dostęp do listy dołączania.

 Jeśli monitowanie jest wyłączone, można zainstalować tylko rozwiązania z zaufanym i znanym certyfikatem. Jeśli poziom monitowania jest wymagany w przypadku opcji Authenticode, rozwiązanie musi być podpisane przy użyciu certyfikatu ze znanego urzędu, ale nie wymaga certyfikatu, który tworzy łańcuch z zaufanym urzędem głównym (zaufany certyfikat). Jeśli monitowanie jest dozwolone, rozwiązanie może być podpisane za pomocą certyfikatu o nieznanej tożsamości. W tym scenariuszu decyzja dotycząca zaufania zostaje odroczona do użytkownika końcowego, a tymczasowy certyfikat będzie wystarczający do zainstalowania rozwiązania.

 Aby uzyskać więcej informacji, zobacz [How to: Configure list dołączania zabezpieczenia](../vsto/how-to-configure-inclusion-list-security.md) i tabela 2, zatytułowane na poziomie monitu dotyczące uruchamiania wartości klucza rejestru, w obszarze [Konfigurowanie zaufanych wydawców ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="structure-of-the-inclusion-list"></a>Struktura listy dołączania
 Prawidłowy wpis listy dołączania ma dwie części: ścieżkę do manifestu wdrażania i klucz publiczny służący do podpisywania rozwiązania. Po dodaniu rozwiązania do listy dołączania jest ono uznawane za zaufane. Po uruchomieniu rozwiązania pakietu Office aplikacja pakietu Office porównuje klucz publiczny z listy dołączania z kluczem podpisywania w manifeście wdrożenia, aby sprawdzić, czy aktualnie uruchomione rozwiązanie jest takie samo, jak w przypadku oryginalnej zaufanej wersji.

## <a name="see-also"></a>Zobacz też
- [Udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
