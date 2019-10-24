---
title: Debuguj aplikację ClickOnce z ograniczonymi uprawnieniami
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
ms.openlocfilehash: 0d942c41aac873b775566efa4e128651a8830e92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727952"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Instrukcje: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami
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

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Bezpieczne aplikacje ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [Bezpieczne aplikacje ClickOnce](../deployment/securing-clickonce-applications.md)