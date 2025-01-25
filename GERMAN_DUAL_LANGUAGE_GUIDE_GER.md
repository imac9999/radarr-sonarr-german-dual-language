## Optimierte Radarr/Sonarr Einrichtung für Deutsch/Englisch

**Grundeinstellungen**
- Erstelle ein neues Quality Profile
- Setze Sprache auf "Any"
- Setze "Upgrade Until Custom" auf 50000
- Merge alle gewünschten Qualitäten (z.B. Remux-1080p bis WebDL-720p)

## Custom Formats

**Sprach-Profile**
```json
{
  "name": "German DL",
  "specifications": [
    {
      "name": "German DL",
      "implementation": "ReleaseTitleSpecification",
      "required": true,
      "fields": {
        "value": "(?i)german\\s*\\.?dl|(?<=\\bGerman\\b.*)(?<!\\bWEB[-_. ])\\bDL\\b|\\[DE\\+[a-z]{2}\\]|\\[[a-z]{2}\\+DE\\]|ger,\\s*[a-z]{3}\\]|\\[[a-z]{3}\\s*,\\s*ger\\]"
      }
    }
  ]
}
```

Importiere das Custom Format "German DL 2":
```json
 {
  "name": "German DL 2",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "NOT German DL",
      "implementation": "ReleaseTitleSpecification",
      "negate": true,
      "required": true,
      "fields": {
        "value": "(?i)german\\s*\\.?dl|(?<=\\bGerman\\b.*)(?<!\\bWEB[-_. ])\\bDL\\b|\\[DE\\+[a-z]{2}\\]|\\[[a-z]{2}\\+DE\\]|ger,\\s*[a-z]{3}\\]|\\[[a-z]{3}\\s*,\\s*ger\\]"
      }
    },
    {
      "name": "German",
      "implementation": "LanguageSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 4
      }
    },
    {
      "name": "English",
      "implementation": "LanguageSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 1
      }
    }
  ]
}
```
Importiere das Custom Format "Language: Not ENG/GER":

```json
{
  "name": "Language: Not ENG/GER",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "Not English Language",
      "implementation": "LanguageSpecification",
      "negate": true,
      "required": true,
      "fields": {
        "value": 1
      }
    },
    {
      "name": "Not German Language",
      "implementation": "LanguageSpecification",
      "negate": true,
      "required": true,
      "fields": {
        "value": 4
      }
    },
    {
      "name": "Not German in Title",
      "implementation": "ReleaseTitleSpecification",
      "negate": true,
      "required": true,
      "fields": {
        "value": "(?i)\\bgerman\\b"
      }
    }
  ]
}
```

Importiere die Custom Formats, die du benötigst:
<details>
<summary><b>Bluray-1080p (Radarr)</b></summary>

```json
{
  "name": "Bluray-1080p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "Bluray",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 9
      }
    },
    {
      "name": "1080p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 1080
      }
    },
    {
      "name": "Not REMUX",
      "implementation": "QualityModifierSpecification",
      "negate": true,
      "required": true,
      "fields": {
        "value": 5
      }
    }
  ]
}
```
</details>

<details>
<summary><b>Bluray-1080p (Sonarr)</b></summary>

```json
{
  "name": "Bluray-1080p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "Bluray",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 6
      }
    },
    {
      "name": "1080p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 1080
      }
    },
    {
      "name": "Not REMUX",
      "implementation": "SourceSpecification",
      "negate": true,
      "required": true,
      "fields": {
        "value": 7
      }
    }
  ]
}
```
</details>

<details>
<summary><b>Bluray-2160p (Radarr)</b></summary>

```json
{
  "name": "Bluray-2160p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "Bluray",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 9
      }
    },
    {
      "name": "2160p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 2160
      }
    },
    {
      "name": "Not REMUX",
      "implementation": "QualityModifierSpecification",
      "negate": true,
      "required": true,
      "fields": {
        "value": 5
      }
    }
  ]
}
```
</details>

<details>
<summary><b>Bluray-2160p (Sonarr)</b></summary>

```json
{
  "name": "Bluray-2160p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "Bluray",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 6
      }
    },
    {
      "name": "2160p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 2160
      }
    },
    {
      "name": "Not REMUX",
      "implementation": "SourceSpecification",
      "negate": true,
      "required": true,
      "fields": {
        "value": 7
      }
    }
  ]
}
```
</details>

<details>
<summary><b>Bluray-720p (Radarr)</b></summary>

```json
{
  "name": "Bluray-720p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "Bluray",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 9
      }
    },
    {
      "name": "720p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 720
      }
    },
    {
      "name": "Not REMUX",
      "implementation": "QualityModifierSpecification",
      "negate": true,
      "required": true,
      "fields": {
        "value": 5
      }
    }
  ]
}
```
</details>

<details>
<summary><b>Bluray-720p (Sonarr)</b></summary>

```json
{
  "name": "Bluray-720p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "Bluray",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 6
      }
    },
    {
      "name": "720p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 720
      }
    },
    {
      "name": "Not REMUX",
      "implementation": "SourceSpecification",
      "negate": true,
      "required": true,
      "fields": {
        "value": 7
      }
    }
  ]
}
```
</details>

<details>
<summary><b>WEBDL-1080p (Radarr)</b></summary>

```json
{
  "name": "WEBDL-1080p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {


      "name": "WEBDL",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 7
      }
    },
    {
      "name": "1080p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 1080
      }
    }
  ]
}
```
</details>

<details>
<summary><b>WEBDL-1080p (Sonarr)</b></summary>

```json
{
  "name": "WEBDL-1080p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {


      "name": "WEBDL",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 3
      }
    },
    {
      "name": "1080p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 1080
      }
    }
  ]
}
```
</details>

<details>
<summary><b>WEBDL-2160p (Radarr)</b></summary>

```json
{
  "name": "WEBDL-2160p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "WEBDL",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 7
      }
    },
    {
      "name": "2160p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 2160
      }
    }
  ]
}
```
</details>


<details>
<summary><b>WEBDL-2160p (Sonarr)</b></summary>

```json
{
  "name": "WEBDL-2160p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "WEBDL",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 3
      }
    },
    {
      "name": "2160p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 2160
      }
    }
  ]
}
```
</details>

<details>
<summary><b>WEBDL-720p (Radarr)</b></summary>

```json
{
  "name": "WEBDL-720p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "WEBDL",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 7
      }
    },
    {
      "name": "720p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 720
      }
    }
  ]
}
```
</details>

<details>
<summary><b>WEBDL-720p (Sonarr)</b></summary>

```json
{
  "name": "WEBDL-720p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "WEBDL",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 3
      }
    },
    {
      "name": "720p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 720
      }
    }
  ]
}
```
</details>

<details>
<summary><b>WebRip-1080p (Radarr)</b></summary>

```json
{
  "name": "WebRip-1080p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "WebRip",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 8
      }
    },
    {
      "name": "1080p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 1080
      }
    }
  ]
}
```
</details>

<details>
<summary><b>WebRip-1080p (Sonarr)</b></summary>

```json
{
  "name": "WebRip-1080p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "WebRip",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 4
      }
    },
    {
      "name": "1080p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 1080
      }
    }
  ]
}
```
</details>

<details>
<summary><b>WebRip-720p (Radarr)</b></summary>

```json
{
  "name": "WebRip-720p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "WebRip",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 8
      }
    },
    {
      "name": "720p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 720
      }
    }
  ]
}
```
</details>

<details>
<summary><b>WebRip-720p (Sonarr)</b></summary>

```json
{
  "name": "WebRip-720p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "WebRip",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 4
      }
    },
    {
      "name": "720p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 720
      }
    }
  ]
}
```
</details>

<details>
<summary><b>Remux-1080p (Radarr)</b></summary>

```json
{
  "name": "Remux-1080p",
  "includeCustomFormatWhenRenaming":

 false,
  "specifications": [
    {
      "name": "1080p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 1080
      }
    },
    {
      "name": "REMUX",
      "implementation": "QualityModifierSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 5
      }
    }
  ]
}
```
</details>

<details>
<summary><b>Remux-1080p (Sonarr)</b></summary>

```json
{
  "name": "Remux-1080p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "Remux",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 7
      }
    },
    {
      "name": "1080p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 1080
      }
    },
    {
      "name": "Not BluRay",
      "implementation": "SourceSpecification",
      "negate": true,
      "required": true,
      "fields": {
        "value": 6
      }
    }
  ]
}
```
</details>

<details>
<summary><b>Remux-2160p (Radarr)</b></summary>

```json
{
  "name": "Remux-2160p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "2160p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 2160
      }
    },
    {
      "name": "REMUX",
      "implementation": "QualityModifierSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 5
      }
    }
  ]
}
```
</details>

<details>
<summary><b>Remux-2160p (Sonarr)</b></summary>

```json
{
  "name": "Remux-2160p",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "Remux",
      "implementation": "SourceSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 7
      }
    },
    {
      "name": "2160p",
      "implementation": "ResolutionSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": 2160
      }
    },
    {
      "name": "Not BluRay",
      "implementation": "SourceSpecification",
      "negate": true,
      "required": true,
      "fields": {
        "value": 6
      }
    }
  ]
}
```
</details>

Importiere das MIC DUB Custom Format:

<details>
<summary><b>MIC DUB Custom Format</b></summary>

```json
{
  "name": "MIC DUB",
  "includeCustomFormatWhenRenaming": true,
  "specifications": [
    {
      "name": "MD",
      "implementation": "ReleaseTitleSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": "((19|20|21)[0-9]{2}).*?(?<=^|[ .-])MD(?=[ .-]|$).*?(?<=^|[ .-])GERMAN(?=[ .-]|$)|((19|20|21)[0-9]{2}).*?(?<=^|[ .-])GERMAN(?=[ .-]|$).*?(?<=^|[ .-])MD(?=[ .-]|$)"
      }
    }
  ]
}
```
</details>

```json
{
  "name": "Audio-Atmos",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "Atmos",
      "implementation": "ReleaseTitleSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": "(?i)atmos|truehd.atmos"
      }
    }
  ]
}
```

```json
{
  "name": "Audio-DTS",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "DTS",
      "implementation": "ReleaseTitleSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": "(?i)dts(.?hd)?(.?ma)?|dts-hd"
      }
    }
  ]
}
```

```json
{
  "name": "Audio-EAC3",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "EAC3",
      "implementation": "ReleaseTitleSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": "(?i)eac3|ddp|e-?ac-?3"
      }
    }
  ]
}
```

```json
{
  "name": "Audio-AC3",
  "includeCustomFormatWhenRenaming": false,
  "specifications": [
    {
      "name": "AC3",
      "implementation": "ReleaseTitleSpecification",
      "negate": false,
      "required": true,
      "fields": {
        "value": "(?i)ac3|dd5.1|dolby.?digital"
      }
    }
  ]
}
```


**Punktevergabe**

| Benutzerdefiniertes Format | Punktzahl |
|---------------------------|-----------|
| German DL | 25000 |
| German DL 2 | 25000 |
| Language: German Only | 10000 |
| Bluray-1080p | 8000 |
| WEBDL-1080p | 7000 |
| WebRip-1080p | 6000 |
| Language: English Only | 5000 |
| Bluray-720p | 4000 |
| WEBDL-720p | 3000 |
| WebRip-720p | 2000 |
| Audio-Atmos | 400 |
| Audio-DTS | 300 |
| Audio-EAC3 | 200 |
| Audio-AC3 | 100 |
| Language: Not ENG/GER | -30000 |
| MIC DUB | -35000 |

## Priorisierung

Die Punktevergabe führt zu folgender Priorisierung:
1. Sprache (German DL > German > English)
2. Bildqualität (Bluray > WEBDL > WebRip)
3. Auflösung (1080p > 720p)
4. Audioqualität (Atmos > DTS > EAC3 > AC3)

**Automatische Upgrades**
- Ein Release wird nur durch ein besseres ersetzt wenn:
  - Es eine bessere Sprachversion ist
  - Bei gleicher Sprache eine bessere Bildqualität hat
  - Bei gleicher Sprache/Bildqualität einen besseren Audiocodec bietet

