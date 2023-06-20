# Home Assistant Lovelace card for DWD warnings
Lovelace card for Home Assistant showing Deutscher Wetterdienst (DWD) warnings.

Prerequisites:
- Enabled sensor integration of [Deutscher Wetterdienst (DWD) Weather Warnings](https://www.home-assistant.io/integrations/dwd_weather_warnings/)

![lovelace_dwdwarnings](dwd-weather-warnings_screenshot.png)


I use a conditional card to hide everything when there are no warnings. Just use your sensor name from your integration and copy&paste as "manual card".

If the date of the `end_time` ("Gültig bis") is equal to the current date, the date gets hidden and only the time is shown.


```
type: conditional
conditions:
  - entity: sensor.dwd_weather_warnings_current_warning_level
    state_not: '0'
card:
  type: markdown
  content: >-
    {% set dwd_sensor = "sensor.dwd_weather_warnings_current_warning_level" %} {% set
    type_to_img = {
      11: "",
      12: "",
      13: "",
      14: "",
      15: "",
      16: "",
      22: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Frost_gelb.png?__blob=normal&v=6",
      24: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Glaette_gelb.png?__blob=normal&v=4",
      31: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_gelb.png?__blob=normal&v=4",
      33: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_ocker.png?__blob=normal&v=4",
      34: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_ocker.png?__blob=normal&v=4",
      36: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_ocker.png?__blob=normal&v=4",
      38: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_ocker.png?__blob=normal&v=4",
      40: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_rot.png?__blob=normal&v=4",
      41: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_lila.png?__blob=normal&v=4",
      42: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_rot.png?__blob=normal&v=4",
      44: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_rot.png?__blob=normal&v=4",
      45: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_lila.png?__blob=normal&v=4",
      46: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_rot.png?__blob=normal&v=4",
      48: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_rot.png?__blob=normal&v=4",
      49: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_lila.png?__blob=normal&v=4",
      51: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Wind_gelb.png?__blob=normal&v=4",
      52: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Wind_ocker.png?__blob=normal&v=4",
      53: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Wind_ocker.png?__blob=normal&v=4",
      54: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Wind_rot.png?__blob=normal&v=4",
      55: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Wind_rot.png?__blob=normal&v=4",
      56: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Wind_lila.png?__blob=normal&v=4",
      57: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Wind_gelb.png?__blob=normal&v=4",
      58: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Wind_ocker.png?__blob=normal&v=4",
      59: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Nebel_gelb.png?__blob=normal&v=4",
      61: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Regen_ocker.png?__blob=normal&v=4",
      62: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Regen_rot.png?__blob=normal&v=4",
      63: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Regen_ocker.png?__blob=normal&v=4",
      64: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Regen_rot.png?__blob=normal&v=4",
      65: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Regen_lila.png?__blob=normal&v=4",
      66: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Regen_lila.png?__blob=normal&v=4",
      70: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Schnee_gelb.png?__blob=normal&v=4",
      71: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Schnee_ocker.png?__blob=normal&v=4",
      72: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Schnee_rot.png?__blob=normal&v=4",
      73: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Schnee_lila.png?__blob=normal&v=4",
      74: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Schnee_ocker.png?__blob=normal&v=4",
      75: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Schnee_rot.png?__blob=normal&v=4",
      76: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Schnee_lila.png?__blob=normal&v=4",
      79: "",
      82: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Frost_ocker.png?__blob=normal&v=4",
      84: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Glaette_gelb.png?__blob=normal&v=4",
      85: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Glaette_ocker.png?__blob=normal&v=4",
      87: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Glaette_rot.png?__blob=normal&v=4",
      88: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Tauwetter_ocker.png?__blob=normal&v=5",
      89: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Tauwetter_rot.png?__blob=normal&v=5",
      90: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_gelb.png?__blob=normal&v=4",
      91: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_ocker.png?__blob=normal&v=4",
      92: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_rot.png?__blob=normal&v=4",
      93: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_lila.png?__blob=normal&v=4",
      95: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_lila.png?__blob=normal&v=4",
      96: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Gewitter_lila.png?__blob=normal&v=4",
      98: "",
      99: "",
      246: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/UV_lila.png?__blob=normal&v=4",
      247: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Hitze_lila.png?__blob=normal&v=5",
      248: "https://www.dwd.de/DE/wetter/warnungen_aktuell/kriterien/pictogramme/Hitze_dunkellila.png?__blob=normal&v=1"}
    %}

    {% for idx in range(1, state_attr(dwd_sensor, "warning_count")+1) %}
      <table width="100%">
        <tr>
          <td>
            <h3>{{ state_attr(dwd_sensor, ("warning_" ~ idx)).headline }}</h3>
          </td>
          <td>
            <img src="{{type_to_img[state_attr(dwd_sensor, ("warning_" ~ idx)).event_code]}}"/>
          </td>
        </tr>
      </table>
      
      {{ state_attr(dwd_sensor, ("warning_" ~ idx)).description }}
      {% set end_time = state_attr(dwd_sensor, ("warning_" ~ idx)).end_time.timestamp() %}
      *Gültig bis {% if end_time | timestamp_custom('%d.%m.%d') != now().timestamp() | timestamp_custom('%d.%m.%d') %}{{ end_time | timestamp_custom('%d.%m.%d, ') }}{% endif %}{{ end_time | timestamp_custom('%H:%M Uhr') }}. Region: {{ state_attr(dwd_sensor, "region_name") }}*
    {% endfor %}

```
