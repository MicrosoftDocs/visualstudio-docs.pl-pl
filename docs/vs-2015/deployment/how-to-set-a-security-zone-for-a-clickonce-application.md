---
title: 'Instrukcje: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9af4507d7ccd604f82aae675bf87d36c0b039b26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68171417"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas ustawiania uprawnień zabezpieczeń dostępu kodu dla aplikacji ClickOnce należy zacząć od podstawowego zestawu uprawnień na stronie **zabezpieczenia** **projektanta projektu**.  
  
 W większości przypadków można również wybrać strefę **internetową** , która zawiera ograniczony zestaw uprawnień lub lokalną strefę **intranetową** , która zawiera większy zestaw uprawnień. Jeśli aplikacja wymaga uprawnień niestandardowych, możesz to zrobić, wybierając **niestandardową** strefę zabezpieczeń. Aby uzyskać więcej informacji o ustawianiu uprawnień niestandardowych, zobacz [How to: Set Custom Permissions for a ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### <a name="to-set-a-security-zone"></a>Aby ustawić strefę zabezpieczeń  
  
1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Kliknij kartę **Zabezpieczenia**.  
  
3. Zaznacz pole wyboru **Włącz ustawienia zabezpieczeń ClickOnce** .  
  
4. Wybierz przycisk opcji **ta jest częściowo zaufana aplikacja** .  
  
     Kontrolki w sekcji **uprawnienia zabezpieczeń ClickOnce** są włączone.  
  
5. W strefie, w której **aplikacja zostanie zainstalowana z** listy rozwijanej, wybierz strefę zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
