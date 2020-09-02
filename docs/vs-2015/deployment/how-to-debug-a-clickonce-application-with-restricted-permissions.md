---
title: 'Instrukcje: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ClickOnce applications
- ClickOnce deployment, debugging
- ClickOnce applications, debugging
ms.assetid: 6991ea91-5253-451b-923d-22273a3d38b1
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d60f88c4d1532a03922f12f21bb9b455ef5d84d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153798"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Porady: debugowanie aplikacji ClickOnce przy użyciu ograniczonych uprawnień
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Deweloperem najprawdopodobniej używasz komputera deweloperskiego z pełnymi uprawnieniami zaufania, więc nie zobaczysz tych samych wyjątków zabezpieczeń podczas debugowania aplikacji ClickOnce, którą użytkownik końcowy może zobaczyć podczas jej uruchamiania z ograniczonymi uprawnieniami.  
  
 Aby przechwytywać te wyjątki, należy debugować aplikację z takimi samymi uprawnieniami jak użytkownik końcowy. Debugowanie z ograniczonymi uprawnieniami można włączyć na stronie **zabezpieczenia** **projektanta projektu**.  
  
 Ponadto podczas tworzenia aplikacji, które wywołują usługi sieci Web, te usługi sieci Web często znajdują się na komputerze deweloperskim. Po wdrożeniu użytkownicy końcowi będą uzyskiwać dostęp do tych usług sieci Web przy użyciu innego adresu URL. Aby emulować środowisko użytkownika końcowego podczas debugowania, można określić adres URL, a debuger będzie traktować usługi sieci Web tak, jakby były wywoływane z tego adresu URL.  
  
### <a name="to-enable-debugging-with-restricted-permissions"></a>Aby włączyć debugowanie z ograniczonymi uprawnieniami  
  
1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.  
  
2. W **projektancie projektu**kliknij kartę **zabezpieczenia** .  
  
3. Zaznacz pole wyboru **Włącz ustawienie zabezpieczeń ClickOnce** , a następnie kliknij przycisk opcji **to jest aplikacja częściowo zaufana** .  
  
4. Kliknij przycisk **Zaawansowane** .  
  
5. Zaznacz pole wyboru **Debuguj tę aplikację z wybranym zestawem uprawnień** , a następnie kliknij przycisk **OK**.  
  
     Gdy debugujesz aplikację, wszelkie próby uzyskania dostępu do uprawnienia, które nie jest częścią zestawu uprawnień spowodują wystąpienie wyjątku zabezpieczeń.  
  
### <a name="to-specify-a-url-for-debugging"></a>Aby określić adres URL do debugowania  
  
1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.  
  
2. W **projektancie projektu**kliknij kartę **zabezpieczenia** .  
  
3. Zaznacz pole wyboru **Włącz ustawienie zabezpieczeń ClickOnce** , a następnie kliknij przycisk opcji **to jest aplikacja częściowo zaufana** .  
  
4. Kliknij przycisk **Zaawansowane** .  
  
5. Zaznacz pole wyboru **Debuguj tę aplikację z wybranym zestawem uprawnień** , a następnie kliknij przycisk **OK**.  
  
6. W polu tekstowym **Debuguj tę aplikację tak, jakby była pobrana z następującego adresu URL** , wprowadź adres URL lub ścieżkę sieciową.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
