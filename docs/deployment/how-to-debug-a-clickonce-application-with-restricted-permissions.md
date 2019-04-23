---
title: 'Instrukcje: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4072cef2a47db1177a8ee7b630bd8febccc5e0b6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60049586"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Instrukcje: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami
Deweloperzy najprawdopodobniej używasz komputer deweloperski przy użyciu uprawnień pełnego zaufania, dzięki czemu nie będą widzieć same wyjątki zabezpieczeń podczas debugowania aplikacji ClickOnce, które użytkownik końcowy może zostać wyświetlony po uruchomieniu z ograniczonymi uprawnieniami.

 Aby przechwytywać te wyjątki, konieczne będzie można debugować aplikację za pomocą tych samych uprawnień jako użytkownik końcowy. Debugowanie przy użyciu ograniczonych uprawnień można włączyć dla **zabezpieczeń** strony **projektanta projektu**.

 Ponadto podczas tworzenia aplikacji, które wywołują usługi sieci Web, te usługi sieci Web często znajdują się na komputerze deweloperskim. Po wdrożeniu, użytkownik końcowy będzie dostęp do tych usług sieci Web z innego adresu URL. Aby emulować doświadczenia użytkownika końcowego podczas debugowania, można określić, że adres URL i debuger traktują usług sieci Web tak, jakby były one wywoływane z tego adresu URL.

### <a name="to-enable-debugging-with-restricted-permissions"></a>Aby włączyć debugowanie z ograniczonymi uprawnieniami

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2. W **projektanta projektu**, kliknij przycisk **zabezpieczeń** kartę.

3. Wybierz **Włącz ustawienie zabezpieczeń ClickOnce** pole wyboru, a następnie kliknij przycisk **to częściowo zaufanych aplikacji** przycisku opcji.

4. Kliknij przycisk **zaawansowane** przycisku.

5. Wybierz **Debuguj aplikację z wybranym zestawem uprawnień** pole wyboru, a następnie kliknij przycisk **OK**.

     Podczas debugowania aplikacji, wszelkie próby uprawnienie, które nie jest częścią zestawu uprawnień dostępu zgłosi wyjątek zabezpieczeń.

### <a name="to-specify-a-url-for-debugging"></a>Aby określić adres URL do debugowania

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2. W **projektanta projektu**, kliknij przycisk **zabezpieczeń** kartę.

3. Wybierz **Włącz ustawienie zabezpieczeń ClickOnce** pole wyboru, a następnie kliknij przycisk **to częściowo zaufanych aplikacji** przycisku opcji.

4. Kliknij przycisk **zaawansowane** przycisku.

5. Wybierz **Debuguj aplikację z wybranym zestawem uprawnień** pole wyboru, a następnie kliknij przycisk **OK**.

6. W **Debuguj aplikację tak, jakby zostały pobrane z następującego adresu URL** polu tekstowym wprowadź adres URL lub ścieżka sieciowa.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)