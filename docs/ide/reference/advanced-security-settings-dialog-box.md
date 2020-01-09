---
title: Zaawansowane ustawienia zabezpieczeń — Okno dialogowe
ms.date: 06/27/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 033c8d9c97d54b972a7bf30e9e1e04171e5b505e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595842"
---
# <a name="advanced-security-settings-dialog-box"></a>Okno dialogowe Zaawansowane ustawienia zabezpieczeń

To okno dialogowe umożliwia określenie ustawień zabezpieczeń związanych z debugowaniem w strefie.

![Zaawansowane ustawienia zabezpieczeń — okno dialogowe w programie Visual Studio](../media/advanced-security-settings.png)

Aby uzyskać dostęp do tego okna dialogowego, wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** kliknij polecenie **Właściwości**. Gdy zostanie wyświetlony **Projektant projektu** , kliknij kartę **zabezpieczenia** . Na stronie **zabezpieczenia** wybierz opcję **Włącz ustawienia zabezpieczeń ClickOnce**, kliknij **to jest aplikacja częściowej relacji zaufania**, a następnie kliknij przycisk **Zaawansowane**.

## <a name="uielement-list"></a>Lista elementów UIElement

**Przyznaj aplikacji dostęp do jej lokalizacji pochodzenia**

Jeśli zaznaczysz to pole wyboru, aplikacja będzie mogła uzyskać dostęp do witryny sieci Web lub udziału serwera, na którym została opublikowana. Ta opcja jest wybrana domyślnie.

**Debuguj tę aplikację tak, jakby była pobrana z następującego adresu URL**

Jeśli musisz zezwolić aplikacji na dostęp do witryny sieci Web lub udziału serwera odpowiadającego **adresowi URL instalacji** określonym na stronie **publikowania** , wprowadź tutaj ten adres URL. Ta opcja jest dostępna tylko w przypadku wybrania opcji **Udziel dostępu aplikacji do jej lokalizacji pochodzenia** .

## <a name="see-also"></a>Zobacz także

- [Strona zabezpieczeń, Projektant projektu](../../ide/reference/security-page-project-designer.md)
