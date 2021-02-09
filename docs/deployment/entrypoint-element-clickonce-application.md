---
title: '&lt;entryPoint — &gt; element (Aplikacja ClickOnce) | Microsoft Docs'
description: Element entryPoint identyfikuje zestaw, który powinien być wykonany, gdy ta aplikacja ClickOnce zostanie uruchomiona na komputerze klienckim.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5c35d94001ae1e883e2bd76650f248d7e0364d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893896"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;entryPoint — &gt; element (Aplikacja ClickOnce)
Identyfikuje zestaw, który ma zostać wykonany po [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uruchomieniu tej aplikacji na komputerze klienckim.

## <a name="syntax"></a>Składnia

```xml
<entryPoint
   name
>
   <assemblyIdentity
      name
      version
      processorArchitecture
      language
   />
   <commandLine
      file
      parameters
   />
   <customHostRequired />
   <customUX />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `entryPoint`Element jest wymagany i znajduje się w `urn:schemas-microsoft-com:asm.v2` przestrzeni nazw. `entryPoint`W manifeście aplikacji może być zdefiniowany tylko jeden element.

 `entryPoint`Element ma następujący atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`name`|Opcjonalny. Ta wartość nie jest używana przez .NET Framework.|

 `entryPoint` ma następujące elementy.

## <a name="assemblyidentity"></a>assemblyIdentity
 Wymagane. Rola `assemblyIdentity` i jej atrybuty są zdefiniowane w [ \<assemblyIdentity> elemencie](../deployment/assemblyidentity-element-clickonce-application.md).

 `processorArchitecture`Atrybut tego elementu i `processorArchitecture` atrybut zdefiniowany w `assemblyIdentity` innym miejscu w manifeście aplikacji musi być zgodny.

## <a name="commandline"></a>Wiersza polecenia
 Wymagane. Musi być elementem podrzędnym `entryPoint` elementu. Nie ma elementów podrzędnych i ma następujące atrybuty.

| Atrybut | Opis |
|--------------| - |
| `file` | Wymagane. Lokalne odwołanie do zestawu startowego dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Ta wartość nie może zawierać separatorów ścieżek ukośników (/) ani ukośników odwrotnych ( \\ ). |
| `parameters` | Wymagane. Opisuje akcję do wykonania z punktem wejścia. Jedyna prawidłowa wartość to `run` ; w przypadku podania pustego ciągu `run` zostanie przyjęty. |

## <a name="customhostrequired"></a>customHostRequired
 Opcjonalny. W przypadku uwzględnienia określa, że to wdrożenie zawiera składnik, który zostanie wdrożony w ramach hosta niestandardowego i nie jest aplikacją autonomiczną.

 Jeśli ten element jest obecny, `assemblyIdentity` elementy i `commandLine` nie mogą być obecne. Jeśli są, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wystąpi błąd walidacji podczas instalacji.

 Ten element nie ma atrybutów ani elementów podrzędnych.

## <a name="customux"></a>customUX
 Opcjonalny. Określa, że aplikacja jest zainstalowana i obsługiwana przez instalatora niestandardowego i nie tworzy wpisu menu Start, skrótu ani apletu Dodaj lub usuń programy.

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 Aplikacja zawierająca element customUX musi dostarczyć Instalator niestandardowy, który używa <xref:System.Deployment.Application.InPlaceHostingManager> klasy do wykonywania operacji instalacji. Nie można zainstalować aplikacji z tym elementem przez dwukrotne kliknięcie jego manifestu lub setup.exe programu inicjującego wymaganego wstępnie. Instalator niestandardowy może tworzyć wpisy menu Start, skróty oraz dodawać lub usuwać wpisy programów. Jeśli Instalator niestandardowy nie utworzy wpisu Dodaj lub usuń programy, musi przechowywać Identyfikator subskrypcji dostarczony przez <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> Właściwość i umożliwić użytkownikowi późniejsze odinstalowanie aplikacji przez wywołanie <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> metody. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie niestandardowego Instalatora dla aplikacji ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).

## <a name="remarks"></a>Uwagi
 Ten element identyfikuje zestaw i punkt wejścia dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

 Nie można użyć `commandLine` do przekazywania parametrów do aplikacji w czasie wykonywania. Można uzyskać dostęp do parametrów ciągu zapytania dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia z poziomu aplikacji <xref:System.AppDomain> . Aby uzyskać więcej informacji, zobacz [How to: pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

## <a name="example"></a>Przykład
 Poniższy przykład kodu ilustruje `entryPoint` element w manifeście aplikacji dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Ten przykład kodu jest częścią większego przykładu dostarczonego w temacie [manifestu aplikacji ClickOnce](../deployment/clickonce-application-manifest.md) .

```xml
<!-- Identify the main code entrypoint. -->
<!-- This code runs the main method in an executable assembly. -->
  <entryPoint>
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
```

## <a name="see-also"></a>Zobacz też
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
