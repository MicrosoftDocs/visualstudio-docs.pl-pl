---
title: Jak ustawić uprawnienia niestandardowe dla aplikacji ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17cd398468bd1640e50f6a58004905cfdf6c2ff0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382149"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Instrukcje: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce
Można wdrożyć [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację, która używa domyślnych uprawnień dla strefy Internet lub lokalny intranet. Alternatywnie można utworzyć strefę niestandardową dla określonych uprawnień wymaganych przez aplikację. Można to zrobić przez dostosowanie uprawnień zabezpieczeń na stronie **zabezpieczenia** **projektanta projektu**.

### <a name="to-customize-a-permission"></a>Aby dostosować uprawnienie

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Zabezpieczenia**.

3. Zaznacz pole wyboru **Włącz ustawienia zabezpieczeń ClickOnce** .

4. Wybierz przycisk opcji **ta jest częściowo zaufana aplikacja** .

     Kontrolki w sekcji **uprawnienia zabezpieczeń ClickOnce** są włączone.

5. Ze strefy, w której **aplikacja zostanie zainstalowana, z** listy rozwijanej kliknij pozycję **(niestandardowe)**.

6. Kliknij pozycję **Edytuj uprawnienia XML**.

     Plik *App. manifest* zostanie otwarty w edytorze XML.

7. Przed `</applicationRequestMinimum>` elementem Dodaj kod XML dla uprawnień wymaganych przez aplikację.

    > [!NOTE]
    > Można użyć `ToXml` metody zestawu uprawnień do generowania kodu XML dla manifestu aplikacji. Na przykład, aby wygenerować plik XML dla <xref:System.Security.Permissions.EnvironmentPermission> zestawu uprawnień, wywołaj <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> metodę.

## <a name="see-also"></a>Zobacz też
- [Bezpieczne aplikacje ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
