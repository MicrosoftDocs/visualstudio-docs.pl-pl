---
title: 'Instrukcje: podpisywanie plików instalacyjnych za pomocą SignTool.exe (ClickOnce) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202180"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Porady: podpisywanie plików konfiguracji przy użyciu narzędzia SignTool.exe (ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą SignTool.exe można podpisać program instalacyjny (setup.exe). Ten proces zapewnia, że naruszone pliki nie są zainstalowane na komputerach użytkowników końcowych.  
  
 Domyślnie technologia ClickOnce ma podpisane manifesty i podpisany program instalacyjny. Jeśli jednak chcesz zmienić parametry programu instalacyjnego później, należy podpisać program instalacyjny później. Jeśli zmienisz parametry po podpisaniu programu instalacyjnego, podpis zostanie uszkodzony.  
  
 Poniższa procedura generuje niepodpisane manifesty i niepodpisany program instalacyjny. Następnie podpisywanie ClickOnce jest włączone w programie Visual Studio w celu wygenerowania podpisanych manifestów. Program instalacyjny jest pozostawiony bez znaku, aby klient mógł podpisać plik wykonywalny własnym certyfikatem.  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Aby wygenerować niepodpisany program instalacyjny i zalogować się później  
  
1. Na komputerze deweloperskim Zainstaluj certyfikat, z którym chcesz podpisać manifest.  
  
2. Wybierz projekt w **Eksplorator rozwiązań**.  
  
3. W menu **projekt** kliknij polecenie właściwości *ProjectName* **Properties**.  
  
4. Na stronie **podpisywanie** Wyczyść **manifesty ClickOnce**.  
  
5. Na stronie **Publikowanie** kliknij pozycję **wymagania wstępne**.  
  
6. Sprawdź, czy wybrano wszystkie wymagania wstępne, a następnie kliknij przycisk **OK**.  
  
7. Na stronie **Publikowanie** Sprawdź ustawienia publikowania, a następnie kliknij pozycję **Opublikuj teraz**.  
  
     Rozwiązanie publikuje niepodpisany manifest aplikacji, niepodpisany manifest wdrożenia, pliki specyficzne dla wersji i niepodpisany program instalacyjny do lokalizacji folderu publikacji.  
  
8. Na stronie **Publikowanie** kliknij pozycję **wymagania wstępne**.  
  
9. W oknie dialogowym **wymagania wstępne** wyczyść pole wyboru **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki**.  
  
10. Na stronie **Publikowanie** Sprawdź ustawienia publikowania, a następnie kliknij pozycję **Opublikuj teraz**.  
  
     Rozwiązanie publikuje podpisany manifest aplikacji, manifest wdrożenia podpisany i pliki specyficzne dla wersji w lokalizacji folderu publikowania. Niepodpisany program instalacyjny nie jest zastępowany przez proces publikowania.  
  
11. W witrynie klienta Otwórz wiersz polecenia.  
  
12. Przejdź do katalogu, który zawiera plik. exe.  
  
13. Podpisz plik exe przy użyciu następującego polecenia:  
  
    ```  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Na przykład aby podpisać program instalacyjny, użyj jednego z następujących poleceń:  
  
    ```  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
