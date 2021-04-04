---
title: Pobieranie zestawu satelickiego na żądanie przy użyciu narzędzia ClickOnce Designer
description: Dowiedz się, jak oznaczyć zestawy satelickie jako opcjonalne przy użyciu narzędzia Projektant i pobrać tylko zestaw, a komputer kliencki musi mieć aktualne ustawienia kultury.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9e9166dbd3d6cd7ba4500e2390bd611a31bcee7b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216881"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Przewodnik: pobieranie zestawów satelickich na żądanie za pomocą interfejsu API wdrażania ClickOnce przy użyciu narzędzia Projektant
Aplikacje Windows Forms można skonfigurować dla wielu kultur przy użyciu zestawów satelickich. *Zestaw satelicki* jest zestawem zawierającym zasoby aplikacji dla kultury innej niż domyślna kultura aplikacji.

 Zgodnie z opisem w temacie [lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md)można uwzględnić wiele zestawów satelickich dla wielu kultur w ramach tego samego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Domyślnie program [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pobierze wszystkie zestawy satelickie we wdrożeniu na komputer kliencki, chociaż jeden klient prawdopodobnie będzie wymagał tylko jednego zestawu satelickiego.

 W tym instruktażu przedstawiono sposób oznaczania zestawów satelickich jako opcjonalnych i pobrania tylko zestawu, który jest wymagany przez komputer kliencki dla bieżących ustawień kultury.

> [!NOTE]
> Do celów testowych Poniższy przykład kodu programowo ustawia kulturę na `ja-JP` . Zapoznaj się z sekcją "następne kroki" w dalszej części tego tematu, aby uzyskać informacje na temat dostosowywania tego kodu dla środowiska produkcyjnego.

### <a name="to-mark-satellite-assemblies-as-optional"></a>Aby oznaczyć zestawy satelickie jako opcjonalne

1. Skompilowanie projektu. Spowoduje to wygenerowanie zestawów satelickich dla wszystkich kultur, do których jest zlokalizowany.

2. Kliknij prawym przyciskiem myszy nazwę projektu w Eksplorator rozwiązań, a następnie kliknij pozycję **Właściwości**.

3. Kliknij kartę **Publikowanie** , a następnie kliknij pozycję **pliki aplikacji**.

4. Zaznacz pole wyboru **Pokaż wszystkie pliki** , aby wyświetlić zestawy satelickie. Domyślnie wszystkie zestawy satelickie zostaną uwzględnione we wdrożeniu i będą widoczne w tym oknie dialogowym.

     Zestaw satelicki będzie miał nazwę w postaci *\<isoCode>\ApplicationName.resources.dll*, gdzie \<isoCode> jest identyfikatorem języka w formacie RFC 1766.

5. Kliknij pozycję **Nowy** na liście **Grupa pobierania** dla każdego identyfikatora języka. Po wyświetleniu monitu o podanie nazwy grupy pobierania wprowadź identyfikator języka. Na przykład dla japońskiego zestawu satelickiego należy określić nazwę grupy pobierania `ja-JP` .

6. Zamknij okno dialogowe **pliki aplikacji** .

### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>Pobieranie zestawów satelickich na żądanie w języku C\#

1. Otwórz plik *program. cs* . Jeśli ten plik nie jest widoczny w Eksplorator rozwiązań, wybierz projekt, a następnie w menu **projekt** kliknij polecenie **Pokaż wszystkie pliki**.

2. Użyj poniższego kodu, aby pobrać odpowiedni zestaw satelicki i uruchomić aplikację.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssemblies/CS/Program.cs" id="Snippet1":::

### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Pobieranie zestawów satelickich na żądanie w Visual Basic

1. W oknie **Właściwości** aplikacji kliknij kartę **aplikacja** .

2. W dolnej części strony karty kliknij pozycję **Wyświetl zdarzenia aplikacji**.

3. Dodaj następujące Importy na początku pliku *ApplicationEvents. vb* .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb" id="Snippet1":::

4. Dodaj poniższy kod do klasy `MyApplication`.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb" id="Snippet2":::

## <a name="next-steps"></a>Następne kroki
 W środowisku produkcyjnym prawdopodobnie trzeba będzie usunąć wiersz w przykładach kodu, które są ustawiane <xref:System.Threading.Thread.CurrentUICulture%2A> na określoną wartość, ponieważ domyślnie maszyny klienckie będą mieć poprawną ustawioną wartość. Gdy aplikacja jest uruchamiana na japońskim komputerze klienckim, na przykład <xref:System.Threading.Thread.CurrentUICulture%2A> będzie `ja-JP` domyślnie. Ustawienie programistyczne jest dobrym sposobem na przetestowanie zestawów satelickich przed wdrożeniem aplikacji.

## <a name="see-also"></a>Zobacz też
- [Przewodnik: pobieranie zestawów satelickich na żądanie przy użyciu interfejsu API wdrażania ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)
- [Lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md)
