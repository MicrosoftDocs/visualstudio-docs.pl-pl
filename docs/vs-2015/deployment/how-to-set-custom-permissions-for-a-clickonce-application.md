---
title: 'Instrukcje: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6739f38e91ce998441c4cfa62453d485a5d370e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697544"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można wdrożyć [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikację, która używa domyślnych uprawnień dla strefy Internet lub lokalny intranet. Alternatywnie można utworzyć strefę niestandardową dla określonych uprawnień wymaganych przez aplikację. Można to zrobić przez dostosowanie uprawnień zabezpieczeń na stronie **zabezpieczenia** **projektanta projektu**.  
  
### <a name="to-customize-a-permission"></a>Aby dostosować uprawnienie  
  
1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Kliknij kartę **Zabezpieczenia**.  
  
3. Zaznacz pole wyboru **Włącz ustawienia zabezpieczeń ClickOnce** .  
  
4. Wybierz przycisk opcji **ta jest częściowo zaufana aplikacja** .  
  
     Kontrolki w sekcji **uprawnienia zabezpieczeń ClickOnce** są włączone.  
  
5. Ze strefy, w której **aplikacja zostanie zainstalowana, z** listy rozwijanej kliknij pozycję **(niestandardowe)**.  
  
6. Kliknij pozycję **Edytuj uprawnienia XML**.  
  
     Plik App. manifest zostanie otwarty w edytorze XML.  
  
7. Przed `</applicationRequestMinimum>` elementem Dodaj kod XML dla uprawnień wymaganych przez aplikację.  
  
    > [!NOTE]
    > Można użyć `ToXml` metody zestawu uprawnień do generowania kodu XML dla manifestu aplikacji. Na przykład, aby wygenerować plik XML dla <xref:System.Security.Permissions.EnvironmentPermission> zestawu uprawnień, wywołaj <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> metodę. Aby uzyskać więcej informacji na temat struktury zestawu uprawnień XML, zobacz [NIB: How to: import a set uprawnień przy użyciu pliku XML](https://msdn.microsoft.com/dea16b54-c108-408a-ac36-cdc05f746236).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
