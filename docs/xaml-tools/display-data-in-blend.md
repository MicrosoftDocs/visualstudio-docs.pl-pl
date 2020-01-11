---
title: Wizualizowanie przykładowych danych w interfejsie użytkownika XAML
titleSuffix: Blend for Visual Studio
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 87d31b6c-4607-4121-bb7d-cfc80390ab93
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0614552bbbadd9a472e0780db6f277d423446966
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886455"
---
# <a name="display-data-in-blend-for-visual-studio"></a>Wyświetlanie danych w Blend for Visual Studio

Przykładowe dane można wyświetlić w projektancie w miarę dostosowywania układu stron. Przykładowe dane można generować od podstaw lub przy użyciu istniejącej klasy. Możesz również nawiązać połączenie z *danymi na żywo* , które pojawiają się w aplikacji po jej uruchomieniu.

> [!NOTE]
> Panel **dane** w programie Blend jest obsługiwany tylko w przypadku projektów przeznaczonych do .NET Framework. Nie jest obsługiwana w przypadku projektów platformy UWP i projektów przeznaczonych dla platformy .NET Core. 

## <a name="generate-sample-data"></a>Generowanie danych przykładowych

Aby wygenerować przykładowe dane, Otwórz dokument XAML. W panelu **dane** ![wybierz przycisk ikony](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) **Utwórz** przykładowe dane Utwórz przykładowe dane, a następnie wybierz pozycję **nowe przykładowe dane**.

Zdefiniuj strukturę danych w panelu **dane** , a następnie powiąż ją z elementami interfejsu użytkownika na dowolnej stronie.

![Panel dane](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png)

Jeśli chcesz, aby dane przykładowe pojawiły się na stronach podczas uruchamiania aplikacji, wybierz pozycję **Opcje źródła danych** ![ikona opcje źródła danych](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png), a następnie wybierz opcję **Włącz przy uruchamianiu aplikacji**.

![Włącz podczas uruchamiania elementu menu aplikacji](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png)

**Obejrzyj krótkie wideo:** ![ikona odtwarzania](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Utwórz przykładowe dane od podstaw](https://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2).

## <a name="generate-sample-data-from-a-class"></a>Generowanie przykładowych danych z klasy

Jeśli już utworzono klasy opisujące strukturę danych, możesz generować przykładowe dane z nich.

Aby wygenerować przykładowe dane z klasy, Otwórz dokument XAML, a następnie w panelu **dane** ![kliknij przycisk](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) ikony **Utwórz** przykładowe dane Utwórz przykładowe dane, a następnie kliknij przycisk **Utwórz przykładowe dane z klasy**.

**Obejrzyj krótkie wideo:** ![ikona odtwarzania](../designers/media/bldadminconsoleinitialconfigicon.PNG) [zamieszać niektóre powiązania danych z programem Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
