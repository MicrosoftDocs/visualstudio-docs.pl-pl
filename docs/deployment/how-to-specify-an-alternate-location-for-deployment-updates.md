---
title: Określ alternatywną lokalizację aktualizacji wdrożenia
description: Dowiedz się, jak określić alternatywną lokalizację dla aktualizacji aplikacji ClickOnce w manifeście wdrożenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 698ca2c97bcc4699d2c836eff9fefa371481c9cc
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349649"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Instrukcje: Określanie alternatywnej lokalizacji aktualizacji wdrożenia
Możesz zainstalować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację początkowo z dysku CD lub udziału plików, ale aplikacja musi sprawdzić, czy aktualizacje są okresowo aktualizowane w sieci Web. Możesz określić alternatywną lokalizację aktualizacji w manifeście wdrożenia, aby aplikacja mogła ją zaktualizować do sieci Web po jej początkowej instalacji.

> [!NOTE]
> Aby można było korzystać z tej funkcji, aplikacja musi być skonfigurowana do instalacji lokalnie. Aby uzyskać więcej informacji, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Ponadto, jeśli zainstalujesz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację z sieci, ustawienie alternatywnej lokalizacji spowoduje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] użycie tej lokalizacji zarówno w przypadku instalacji początkowej, jak i wszystkich kolejnych aktualizacji. Jeśli aplikacja jest instalowana lokalnie (na przykład z dysku CD), początkowa instalacja jest przeprowadzana przy użyciu oryginalnego nośnika, a wszystkie kolejne aktualizacje będą korzystały z lokalizacji alternatywnej.

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Określ alternatywną lokalizację aktualizacji za pomocą MageUI.exe (Narzędzie oparte na Windows Forms)

1. Otwórz .NET Framework wiersz polecenia i wpisz:

     **mageui.exe**

2. W menu **plik** wybierz polecenie **Otwórz** , aby otworzyć manifest wdrożenia aplikacji.

3. Wybierz kartę **Opcje wdrażania** .

4. W polu tekstowym o nazwie **Lokalizacja uruchamiania** wprowadź adres URL katalogu, który będzie zawierać manifest wdrożenia dla aktualizacji aplikacji.

5. Zapisz manifest wdrożenia.

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Określ alternatywną lokalizację aktualizacji za pomocą Mage.exe

1. Otwórz wiersz polecenia .NET Framework.

2. Ustaw lokalizację aktualizacji przy użyciu następującego polecenia. W tym przykładzie *HelloWorld.exe. Application* to ścieżka do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikacji, która zawsze ma rozszerzenie. Application i `http://adatum.com/Update/Path` jest adresem URL, który [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] będzie sprawdzać dostępność aktualizacji aplikacji.

    **Mage — aktualizacja HelloWorld.exe. Application-ProviderUrl http: \/ /adatum.com/Update/Path**

3. Zapisz plik.

   > [!NOTE]
   > Teraz musisz ponownie podpisać plik za pomocą *Mage.exe*. Aby uzyskać więcej informacji, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework
 W przypadku instalowania aplikacji z nośnika w trybie offline, takiego jak dysk CD, a komputer jest w trybie online, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] należy najpierw sprawdzić adres URL określony przez `<deploymentProvider>` tag w manifeście wdrożenia, aby określić, czy lokalizacja aktualizacji zawiera nowszą wersję aplikacji. Jeśli tak, program [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zainstaluje aplikację bezpośrednio z tego miejsca, zamiast z katalogu instalacji początkowej, a środowisko uruchomieniowe języka wspólnego (CLR) określi poziom zaufania aplikacji przy użyciu `<deploymentProvider>` . Jeśli komputer jest w trybie offline lub `<deploymentProvider>` jest nieosiągalny, program jest [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalowany z dysku CD, a środowisko CLR przyznaje zaufanie na podstawie punktu instalacji; w przypadku instalacji z dysku CD oznacza to, że aplikacja otrzymuje pełne zaufanie. Wszystkie kolejne aktualizacje będą dziedziczyć ten poziom zaufania.

 Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje, które używają, `<deploymentProvider>` powinny jawnie zadeklarować wymagane uprawnienia w manifeście aplikacji, tak aby aplikacja nie otrzymywała różnych poziomów zaufania na różnych komputerach.

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)