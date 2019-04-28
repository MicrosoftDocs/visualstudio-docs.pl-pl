---
title: 'Instrukcje: Włączenie ustawień zabezpieczeń technologii ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e52acc18aa18873076df3d02071616c0399b1f33
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407118"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Instrukcje: Włączenie ustawień zabezpieczeń technologii ClickOnce
Zabezpieczenia dostępu kodu dla aplikacji ClickOnce musi być włączony, aby można było opublikować aplikację. Odbywa się to automatycznie podczas publikowania aplikacji za pomocą Kreatora publikacji.

 W niektórych przypadkach włączenie zabezpieczeń dostępu kodu może wpłynąć na wydajność podczas kompilowania lub debugowania aplikacji; w takich przypadkach mogą chcieć tymczasowo wyłączyć ustawienia zabezpieczeń.

 Ustawień zabezpieczeń technologii ClickOnce można włączać lub wyłączać na **zabezpieczeń** strony **projektanta projektu**.

### <a name="to-enable-clickonce-security-settings"></a>Aby włączyć ustawień zabezpieczeń technologii ClickOnce

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2. Kliknij przycisk **zabezpieczeń** kartę.

3. Wybierz **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru.

     Możesz teraz dostosować ustawienia zabezpieczeń dla aplikacji na stronie zabezpieczenia.

    > [!NOTE]
    > To pole wyboru jest wybierana z każdym opublikowaniu aplikacji za pomocą **Publikuj** kreatora.

### <a name="to-disable-clickonce-security-settings"></a>Aby wyłączyć ustawień zabezpieczeń technologii ClickOnce

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2. Kliknij przycisk **zabezpieczeń** kartę.

3. Wyczyść **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru.

     Twoja aplikacja będzie uruchamiana za pomocą ustawień zabezpieczeń w trybie pełnego zaufania; wszystkie ustawienia na **zabezpieczeń** strony zostaną zignorowane.

    > [!NOTE]
    > Każdorazowo, gdy aplikacja została opublikowana przy użyciu Kreatora publikowania tego pola wyboru zostanie wybrany; należy usunąć je ponownie po każdej publikacji pomyślnie.

## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
