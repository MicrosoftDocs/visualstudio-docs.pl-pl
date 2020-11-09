---
title: '&lt;Deployment — &gt; element (wdrożenie ClickOnce) | Microsoft Docs'
description: Element Deployment identyfikuje atrybuty używane do wdrożenia aktualizacji i ekspozycji na system.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 3252c8f305b97564b8fb19affa83cc7dd837c97d
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382861"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;Deployment — &gt; element (wdrażanie ClickOnce)
Identyfikuje atrybuty używane do wdrożenia aktualizacji i ekspozycji na system.

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

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `deployment`Element jest wymagany i znajduje się w `urn:schemas-microsoft-com:asm.v2` przestrzeni nazw. Element ma następujące atrybuty.

| Atrybut | Opis |
|--------------------------| - |
| `install` | Wymagane. Określa, czy ta aplikacja definiuje obecność w menu **Start** systemu Windows, a także w aplecie **Dodaj lub usuń programy** w panelu sterowania. Prawidłowe wartości to `true` i `false` . Jeśli `false` program, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] program zawsze będzie uruchamiał najnowszą wersję tej aplikacji z sieci i nie rozpozna `subscription` elementu. |
| `minimumRequiredVersion` | Opcjonalny. Określa minimalną wersję tej aplikacji, która może być uruchamiana na kliencie programu. Jeśli numer wersji aplikacji jest mniejszy niż numer wersji podany w manifeście wdrożenia, aplikacja nie zostanie uruchomiona. Numery wersji muszą być określone w formacie `N.N.N.N` , gdzie `N` jest liczbą całkowitą bez znaku. Jeśli `install` atrybut ma wartość `false` , `minimumRequiredVersion` nie może być ustawiony. |
| `mapFileExtensions` | Opcjonalny. Wartość domyślna to `false` . Jeśli `true` wszystkie pliki we wdrożeniu muszą mieć rozszerzenie. deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] spowoduje rozszerzenie tego rozszerzenia o te pliki natychmiast po ich pobraniu z serwera sieci Web. W przypadku publikowania aplikacji za pomocą programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] program automatycznie dodaje to rozszerzenie do wszystkich plików. Ten parametr umożliwia pobranie wszystkich plików w ramach [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia z serwera sieci Web, który blokuje przesyłanie plików kończących się na rozszerzeniach "niebezpiecznych", takich jak. exe. |
| `disallowUrlActivation` | Opcjonalny. Wartość domyślna to `false` . Jeśli `true` program uniemożliwia uruchomienie zainstalowanej aplikacji przez kliknięcie adresu URL lub wprowadzenie adresu URL do programu Internet Explorer. Jeśli `install` atrybut nie jest obecny, ten atrybut jest ignorowany. |
| `trustURLParameters` | Opcjonalny. Wartość domyślna to `false` . Jeśli `true` , umożliwia adres URL zawierający parametry ciągu zapytania, które są przesyłane do aplikacji, podobnie jak argumenty wiersza polecenia są przesyłane do aplikacji wiersza polecenia. Aby uzyskać więcej informacji, zobacz [How to: pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Jeśli `disallowUrlActivation` atrybut jest `true` , `trustUrlParameters` musi być wykluczony z manifestu lub jawnie ustawiony na `false` . |

 `deployment`Element zawiera również następujące elementy podrzędne.

## <a name="subscription"></a>subskrypcja
 Opcjonalny. Zawiera `update` element. `subscription`Element nie ma żadnych atrybutów. Jeśli `subscription` element nie istnieje, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja nigdy nie skanuje w poszukiwaniu aktualizacji. Jeśli `install` atrybut `deployment` elementu to `false` , `subscription` element jest ignorowany, ponieważ [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja uruchamiana z sieci zawsze używa najnowszej wersji.

## <a name="update"></a>update
 Wymagane. Ten element jest elementem podrzędnym `subscription` elementu i zawiera `beforeApplicationStartup` `expiration` element lub. `beforeApplicationStartup``expiration`nie można jednocześnie określić w tym samym manifeście wdrożenia.

 `update`Element nie ma żadnych atrybutów.

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 Opcjonalny. Ten element jest elementem podrzędnym `update` elementu i nie ma żadnych atrybutów. Gdy `beforeApplicationStartup` element istnieje, aplikacja zostanie zablokowana podczas [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sprawdzania dostępności aktualizacji, jeśli klient jest w trybie online. Jeśli ten element nie istnieje, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] program najpierw przeskanuje w poszukiwaniu aktualizacji na podstawie wartości określonych dla `expiration` elementu. `beforeApplicationStartup``expiration`nie można jednocześnie określić w tym samym manifeście wdrożenia.

## <a name="expiration"></a>datę
 Opcjonalny. Ten element jest elementem podrzędnym `update` elementu i nie ma elementów podrzędnych. `beforeApplicationStartup``expiration`nie można jednocześnie określić w tym samym manifeście wdrożenia. Gdy zostanie przeprowadzone sprawdzanie aktualizacji i zostanie wykryta zaktualizowana wersja, Nowa wersja pamięci podręcznej zostanie uruchomiona podczas uruchamiania istniejącej wersji. Nowa wersja zostanie zainstalowana po następnym uruchomieniu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

 `expiration`Element obsługuje następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`maximumAge`|Wymagane. Określa, jak stara Bieżąca aktualizacja powinna stać się przed wykonaniem kontroli aktualizacji przez aplikację. Jednostka czasu jest określana przez `unit` atrybut.|
|`unit`|Wymagane. Określa jednostkę czasu dla `maximumAge` . Prawidłowe jednostki to `hours` , `days` , i `weeks` .|

## <a name="deploymentprovider"></a>deploymentProvider
 W przypadku .NET Framework 2,0 ten element jest wymagany, Jeśli manifest wdrożenia zawiera `subscription` sekcję. Dla .NET Framework 3,5 i nowszych ten element jest opcjonalny i domyślnie zostanie umieszczony na serwerze i ścieżce do pliku, w którym został odnaleziony manifest wdrożenia.

 Ten element jest elementem podrzędnym `deployment` elementu i ma następujący atrybut.

| Atrybut | Opis |
|------------| - |
| `codebase` | Wymagane. Identyfikuje lokalizację, jako Uniform Resource Identifier (identyfikator URI) manifestu wdrażania, który jest używany do aktualizowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Ten element umożliwia również przekazywanie lokalizacji aktualizacji na potrzeby instalacji z dysku CD. Musi być prawidłowym identyfikatorem URI. |

## <a name="remarks"></a>Uwagi
 Można skonfigurować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację do skanowania pod kątem aktualizacji podczas uruchamiania, skanowania pod kątem aktualizacji po uruchomieniu lub nigdy nie sprawdzać dostępności aktualizacji. Aby przeprowadzić skanowanie w poszukiwaniu aktualizacji przy uruchamianiu, upewnij się, że `beforeApplicationStartup` element istnieje w `update` elemencie. Aby przeprowadzić skanowanie w poszukiwaniu aktualizacji po uruchomieniu, upewnij się, że `expiration` element istnieje w `update` elemencie i że zostały podane interwały aktualizacji.

 Aby wyłączyć sprawdzanie aktualizacji, Usuń `subscription` element. W przypadku określenia w manifeście wdrożenia, aby nigdy nie skanować w poszukiwaniu aktualizacji, można nadal ręcznie sprawdzać dostępność aktualizacji przy użyciu <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> metody.

 Aby uzyskać więcej informacji o tym, jak deploymentProvider odnosi się do aktualizacji, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="examples"></a>Przykłady
 Poniższy przykład kodu ilustruje `deployment` element w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeście wdrożenia. W przykładzie używa `deploymentProvider` elementu, aby wskazać preferowaną lokalizację aktualizacji.

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

## <a name="see-also"></a>Zobacz też
- [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)