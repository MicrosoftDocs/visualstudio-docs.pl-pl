---
title: Zmień język publikowania dla aplikacji ClickOnce
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0252cf39f8f5ee268adbf625f03a9b5a305b903a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382591"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Instrukcje: Zmienianie języka publikacji dla aplikacji ClickOnce

Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji interfejs użytkownika wyświetlany podczas instalacji domyślnie jest językiem i kulturą komputera deweloperskiego. W przypadku publikowania zlokalizowanej aplikacji należy określić język i kulturę, aby odpowiadały wersji zlokalizowanej. Jest to określane przez `Publish language` Właściwość projektu.

`Publish language`Właściwość można ustawić w oknie dialogowym **Opcje publikowania** dostępnym na stronie **Publikuj** w **projektancie projektu**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>Aby zmienić język publikacji

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. Kliknij przycisk **Opcje** , aby otworzyć okno dialogowe **Opcje publikowania** .

4. Kliknij pozycję **Opis**.

5. W oknie dialogowym **Opcje publikowania** wybierz język i kulturę z listy rozwijanej **Język publikowania** , a następnie kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też

- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)