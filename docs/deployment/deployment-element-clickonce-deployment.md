---
title: '&lt;wdrożenie&gt; — Element (wdrażanie ClickOnce) | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90168dd760ba5619e2d50c864f54122b01ed66fa
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667212"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;wdrożenie&gt; — element (wdrażanie ClickOnce)
Określa atrybuty, używany do wdrażania aktualizacji i ograniczyć narażenie na system.

## <a name="syntax"></a>Składnia

```xml

      <deployment
   install
   minimumRequiredVersion
   mapFileExtensions
   disallowUrlActivation
   trustUrlParameters
>
   <subscription>
         <update>
            <beforeApplicationStartup/>
            <expiration
               maximumAge
               unit
            />
         </update>
   </subscription>
   <deploymentProvider
      codebase
   />
</deployment>
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `deployment` Element jest wymagany i znajduje się w `urn:schemas-microsoft-com:asm.v1` przestrzeni nazw. Element ma następujące atrybuty.

| Atrybut | Opis |
|--------------------------| - |
| `install` | Wymagana. Określa czy ta aplikacja jest obecna na Windows **Start** menu i w Panelu sterowania **apletu Dodaj lub usuń programy** aplikacji. Prawidłowe wartości to `true` i `false`. Jeśli `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] najnowszą wersję tej aplikacji będzie zawsze uruchamiana z sieci, a nie rozpoznaje `subscription` elementu. |
| `minimumRequiredVersion` | Opcjonalna. Określa minimalną wersję tej aplikacji, które można uruchomić na komputerze klienckim. Jeśli numer wersji aplikacji jest mniejszy niż podany w pliku manifestu wdrożenia numer wersji, aplikacja nie będzie działać. Numer wersji musi być określona w formacie `N.N.N.N`, gdzie `N` jest liczbą całkowitą bez znaku. Jeśli `install` atrybut jest `false`, `minimumRequiredVersion` nie może być ustawiony. |
| `mapFileExtensions` | Opcjonalna. Wartość domyślna to `false`. Jeśli `true`, wszystkie pliki we wdrożeniu musi mieć rozszerzenie .deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] będzie paska to rozszerzenie tych plików, jak najszybciej pobiera je z serwera sieci Web. W przypadku publikowania aplikacji za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], automatycznie doda to rozszerzenie do wszystkich plików. Ten parametr umożliwia wszystkich plików w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia mają być pobrane z serwera sieci Web, która blokuje przekazywania plików kończące się na "niebezpieczny" rozszerzeń, takich jak .exe. |
| `disallowUrlActivation` | Opcjonalna. Wartość domyślna to `false`. Jeśli `true`, uniemożliwia zainstalowanej aplikacji po uruchomieniu, klikając adres URL lub wprowadzić adres URL w programie Internet Explorer. Jeśli `install` atrybut nie jest obecny, atrybut ten jest ignorowany. |
| `trustURLParameters` | Opcjonalna. Wartość domyślna to `false`. Jeśli `true`, zezwala na adres URL, aby zawierać parametrów ciągu zapytania, które są przekazywane do aplikacji, wiele podobnych argumenty wiersza polecenia są przekazywane do wiersza polecenia aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie Online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Jeśli `disallowUrlActivation` atrybut jest `true`, `trustUrlParameters` być wykluczone z manifestu, lub jawnie ustawione na `false`. |

 `deployment` Element zawiera także następujących elementów podrzędnych.

## <a name="subscription"></a>subskrypcja
 Opcjonalna. Zawiera `update` elementu. `subscription` Element nie ma żadnych atrybutów. Jeśli `subscription` element nie istnieje, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji nigdy nie rozpocznie skanowanie aktualizacji. Jeśli `install` atrybutu `deployment` element jest `false`, `subscription` element jest ignorowany, ponieważ [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, który jest zawsze uruchamiany z sieci korzysta z najnowszej wersji.

## <a name="update"></a>update
 Wymagana. Ten element jest elementem podrzędnym `subscription` elementu i zawierają dowolne `beforeApplicationStartup` lub `expiration` elementu. `beforeApplicationStartup` i `expiration` nie można określić w tym samym manifestu wdrożenia.

 `update` Element nie ma żadnych atrybutów.

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 Opcjonalna. Ten element jest elementem podrzędnym `update` elementu i nie ma żadnych atrybutów. Gdy `beforeApplicationStartup` element istnieje, że aplikacja będzie zablokowana, gdy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sprawdza dostępność aktualizacji, jeśli klient jest w trybie online. Jeśli ten element nie istnieje, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] najpierw rozpocznie skanowanie aktualizacji, na podstawie wartości określone dla `expiration` elementu. `beforeApplicationStartup` i `expiration` nie można określić w tym samym manifestu wdrożenia.

## <a name="expiration"></a>wygaśnięcie
 Opcjonalna. Ten element jest elementem podrzędnym `update` elementu, a nie ma elementów podrzędnych. `beforeApplicationStartup` i `expiration` nie można określić w tym samym manifestu wdrożenia. Gdy sprawdzanie aktualizacji jest wykonywane, i jest dostępna zaktualizowana wersja zostanie wykryte, nowa wersja zapisuje w pamięci podręcznej podczas uruchamiania istniejącą wersję. Następnie zainstalowaniu nowej wersji przy następnym uruchomieniu programu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

 `expiration` Element obsługuje następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`maximumAge`|Wymagana. Określa, ile lat bieżącej aktualizacji powinna stać się przed aplikacja wykonuje sprawdzenie dostępności aktualizacji. Jednostka czasu jest określany przez `unit` atrybutu.|
|`unit`|Wymagana. Określa jednostkę czasu `maximumAge`. Prawidłowe jednostki są `hours`, `days`, i `weeks`.|

## <a name="deploymentprovider"></a>deploymentProvider
 Dla programu .NET Framework 2.0, ten element jest wymagany, jeśli manifest wdrożenia zawiera `subscription` sekcji. Programu .NET Framework 3.5 lub nowszy ten element jest opcjonalny i domyślnie do serwera i ścieżki pliku, w którym zostało wykryte manifestu wdrażania.

 Ten element jest elementem podrzędnym `deployment` elementu i ma następujący atrybut.

| Atrybut | Opis |
|------------| - |
| `codebase` | Wymagana. Określa lokalizację, jako jednolity identyfikator zasobów (URI), manifest wdrożenia, który służy do aktualizowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Ten element umożliwia również przekazywanie lokalizacji aktualizacji do instalacji na dysku CD. Musi być prawidłowym identyfikatorem URI. |

## <a name="remarks"></a>Uwagi
 Można skonfigurować usługi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji w celu skanowania w poszukiwaniu aktualizacji uruchamianie skanowania w poszukiwaniu aktualizacji po uruchomieniu lub nigdy nie sprawdzaj, czy są aktualizacje. Do skanowania w poszukiwaniu aktualizacji podczas uruchamiania, upewnij się, że `beforeApplicationStartup` element istnieje w ramach `update` elementu. Do skanowania w poszukiwaniu aktualizacji po uruchomieniu, upewnij się, że `expiration` element istnieje w ramach `update` elementu, a podano interwały aktualizacji.

 Aby wyłączyć sprawdzanie dostępności aktualizacji, należy usunąć `subscription` elementu. Po określeniu w pliku manifestu wdrożenia, aby nigdy nie skanowanie w poszukiwaniu aktualizacji, możesz nadal ręcznie sprawdzić aktualizacje za pomocą <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> metody.

 Aby uzyskać więcej informacji na temat sposobu deploymentProvider odnosi się do aktualizacji, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="examples"></a>Przykłady
 W poniższym przykładzie kodu pokazano `deployment` element [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrożenia. W przykładzie użyto `deploymentProvider` element, aby wskazać lokalizację preferowanego aktualizacji.

```xml
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">
    <subscription>
      <update>
        <expiration maximumAge="6" unit="hours" />
      </update>
    </subscription>
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />
  </deployment>
```

## <a name="see-also"></a>Zobacz także
- [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)