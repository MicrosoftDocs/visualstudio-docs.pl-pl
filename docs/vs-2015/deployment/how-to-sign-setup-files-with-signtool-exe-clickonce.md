---
title: 'Instrukcje: Znak plików konfiguracji przy użyciu SignTool.exe (ClickOnce) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 67dc8e858a8ee87ee9e1fef9d99bf24ea4994960
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053211"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Instrukcje: Podpisywanie plików konfiguracji przy użyciu narzędzia SignTool.exe (ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SignTool.exe służy do podpisywania Instalatora (setup.exe). Ten proces pozwala upewnić się, że zmodyfikowany pliki nie są zainstalowane na komputerach użytkowników końcowych.  
  
 Domyślnie ClickOnce zalogował się manifestów i podpisem program instalacyjny. Jednak jeśli chcesz zmienić parametry Instalatora później, należy zalogować się Instalatora później. Jeśli zmienisz parametry po podpisaniu program instalacyjny, podpis jest uszkodzony.  
  
 Poniższa procedura generuje nieoznaczone manifesty i bez znaku program instalacyjny. Następnie w celu wygenerowania podpisanych manifestów podpisywanie ClickOnce jest włączone w programie Visual Studio. Pozostało program instalacyjny bez znaku, dzięki czemu klient może zarejestrować plik wykonywalny przy użyciu ich własnych certyfikatów.  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Aby generować niepodpisane program instalacyjny i podpisać później  
  
1. Na komputerze deweloperskim, należy zainstalować certyfikat, który ma znak manifesty za pomocą.  
  
2. Wybierz projekt w **Eksploratora rozwiązań**.  
  
3. Na **projektu** menu, kliknij przycisk *ProjectName* **właściwości**.  
  
4. W **podpisywanie** strony, wyczyść **Podpisz manifesty ClickOnce**.  
  
5. W **Publikuj** kliknij **wymagania wstępne**.  
  
6. Sprawdź, czy wszystkie wymagania wstępne są zaznaczone, a następnie kliknij **OK**.  
  
7. W **Publikuj** strony, sprawdź ustawienia publikowania, a następnie kliknij przycisk **Publikuj teraz**.  
  
     Rozwiązanie publikuje manifest aplikacji bez znaku, manifest wdrożenia bez znaku, specyficzny dla wersji plików i bez znaku program instalacyjny do publikowania lokalizacji folderu.  
  
8. W **Publikuj** kliknij **wymagania wstępne**.  
  
9. W **wymagania wstępne** okno dialogowe wyczyść **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki**.  
  
10. W **Publikuj** strony, sprawdź ustawienia publikowania, a następnie kliknij przycisk **Publikuj teraz**.  
  
     Rozwiązanie publikuje manifest podpisaną aplikację, manifest wdrożenia podpisane i specyficzny dla wersji plików do publikowania lokalizacji folderu. Niepodpisane program instalacyjny nie jest zastępowany przez proces publikowania.  
  
11. W lokacji klienta otwórz wiersz polecenia.  
  
12. Przejdź do katalogu, który zawiera plik .exe.  
  
13. Podpisz plik .exe, za pomocą następującego polecenia:  
  
    ```  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Na przykład aby zarejestrować program instalacyjny, użyj jednej z następujących poleceń:  
  
    ```  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Ponowne podpisywanie manifestów wdrożenia i aplikacji](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
