---
title: Pobierz zestaw satelicki na żądanie z interfejsem API wdrażania ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34cde3a2444525e48455e445894fd5ab1c66fab8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "66262970"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Przewodnik: pobieranie zestawów satelickich na żądanie przy użyciu interfejsu API wdrażania ClickOnce
Aplikacje Windows Forms można skonfigurować dla wielu kultur przy użyciu zestawów satelickich. *Zestaw satelicki* jest zestawem zawierającym zasoby aplikacji dla kultury innej niż domyślna kultura aplikacji.

 Zgodnie z opisem w temacie [lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md)można uwzględnić wiele zestawów satelickich dla wielu kultur w ramach tego samego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Domyślnie program [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pobierze wszystkie zestawy satelickie we wdrożeniu na komputer kliencki, chociaż jeden klient prawdopodobnie będzie wymagał tylko jednego zestawu satelickiego.

 W tym instruktażu przedstawiono sposób oznaczania zestawów satelickich jako opcjonalnych i pobrania tylko zestawu, który jest wymagany przez komputer kliencki dla bieżących ustawień kultury. Poniższa procedura zawiera narzędzia dostępne w narzędziu [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . To zadanie można także wykonać w temacie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Zobacz również [Przewodnik: pobieranie zestawów satelickich na żądanie za pomocą interfejsu API wdrażania ClickOnce przy użyciu narzędzia Projektant](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) lub [Przewodnik: pobieranie zestawów satelickich na żądanie za pomocą interfejsu API wdrażania ClickOnce przy użyciu narzędzia Projektant](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).

> [!NOTE]
> W celach testowych Poniższy przykładowy kod programowo ustawia kulturę na `ja-JP` . Zapoznaj się z sekcją "następne kroki" w dalszej części tego tematu, aby uzyskać informacje na temat dostosowywania tego kodu dla środowiska produkcyjnego.

## <a name="prerequisites"></a>Wymagania wstępne
 W tym temacie założono, że wiesz, jak dodać zlokalizowane zasoby do aplikacji przy użyciu programu Visual Studio. Aby uzyskać szczegółowe instrukcje, zobacz [Przewodnik: Lokalizowanie formularzy systemu Windows](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100)).

### <a name="to-download-satellite-assemblies-on-demand"></a>Pobieranie zestawów satelickich na żądanie

1. Dodaj następujący kod do aplikacji, aby umożliwić pobieranie zestawów satelickich na żądanie.

    [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
    [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]

2. Generowanie zestawów satelickich dla aplikacji przy użyciu [Resgen.exe (Generator plików zasobów)](/dotnet/framework/tools/resgen-exe-resource-file-generator) lub [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

3. Wygeneruj manifest aplikacji lub Otwórz istniejący manifest aplikacji przy użyciu *MageUI.exe*. Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [MageUI.exe (narzędzie tworzenia i edycji manifestów, klient graficzny)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

4. Kliknij kartę **pliki** .

5. Kliknij przycisk **wielokropka** (**...**) i wybierz katalog zawierający wszystkie zestawy i pliki aplikacji, w tym zestawy satelickie, które zostały wygenerowane przy użyciu *Resgen.exe*. (Zestaw satelicki będzie miał nazwę w postaci * \<isoCode>\ApplicationName.resources.dll*, gdzie \<isoCode> jest identyfikatorem języka w formacie RFC 1766).

6. Kliknij przycisk **Wypełnij** , aby dodać pliki do wdrożenia.

7. Zaznacz pole wyboru **opcjonalne** dla każdego zestawu satelickiego.

8. Ustaw pole grupy dla każdego zestawu satelickiego na jego identyfikator języka ISO. Na przykład dla japońskiego zestawu satelickiego należy określić nazwę grupy pobierania `ja-JP` . Spowoduje to włączenie kodu dodanego w kroku 1 w celu pobrania odpowiedniego zestawu satelickiego, w zależności od <xref:System.Threading.Thread.CurrentUICulture%2A> Ustawienia właściwości użytkownika.

## <a name="next-steps"></a>Następne kroki
 W środowisku produkcyjnym prawdopodobnie trzeba będzie usunąć wiersz w przykładowym kodzie, który <xref:System.Threading.Thread.CurrentUICulture%2A> ma ustawioną określoną wartość, ponieważ domyślnie maszyny klienckie będą mieć prawidłową wartość. Gdy aplikacja jest uruchamiana na japońskim komputerze klienckim, na przykład <xref:System.Threading.Thread.CurrentUICulture%2A> będzie `ja-JP` domyślnie. Ustawienie tej wartości programowo jest dobrym sposobem na testowanie zestawów satelickich przed wdrożeniem aplikacji.

## <a name="see-also"></a>Zobacz też
- [Lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md)
