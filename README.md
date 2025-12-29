{
  "description": "Market Share Evolution com labels acima das linhas e nomes no final",
  "width": 800,
  "height": 500,
  "data": {"name": "dataset"},
  "transform": [
    {
      "calculate": "datum['Market Share (%)'] / 100",
      "as": "Proportion"
    }
  ],
  "layer": [
    {
      "mark": {
        "type": "line",
        "interpolate": "linear",
        "strokeWidth": 3
      },
      "encoding": {
        "x": {
          "field": "Trimestre",
          "type": "nominal",
          "sort": ["3Q22", "3Q23", "3Q24", "3Q25"],
          "axis": {"labelAngle": 0, "title": null}
        },
        "y": {
          "field": "Proportion",
          "type": "quantitative",
          "axis": {"title": null, "labels": false, "ticks": false, "grid": false}
        },
        "color": {
          "field": "Banco/Grupo",
          "type": "nominal",
          "scale": {
            "domain": ["Itaú", "NU", "Bradesco", "Santander", "Digitais", "Bancos de Nichos", "Cooperativas", "Demais", "X"],
            "range": ["#f47721", "#8a05be", "#ffab00", "#db0014", "#00a650", "#00b0e4", "#008000", "#a9a9a9", "#0000ff"]
          },
          "legend": null
        },
        "detail": {"field": "Banco/Grupo"}
      }
    },
    {
      "mark": {
        "type": "text",
        "align": "center",
        "baseline": "bottom",
        "dy": -8,
        "fontSize": 12,
        "fontWeight": "bold",
        "background": "white",
        "padding": 4,
        "cornerRadius": 4
      },
      "encoding": {
        "x": {
          "field": "Trimestre",
          "type": "nominal"
        },
        "y": {
          "field": "Proportion",
          "type": "quantitative"
        },
        "text": {
          "field": "Proportion",
          "type": "quantitative",
          "format": ".1%"
        },
        "color": {
          "field": "Banco/Grupo",
          "type": "nominal"
        }
      }
    },
    {
      "transform": [
        {
          "filter": "datum.Trimestre == '3Q25'"
        }
      ],
      "mark": {
        "type": "text",
        "align": "left",
        "baseline": "middle",
        "dx": 5,
        "fontSize": 12,
        "fontWeight": "bold"
      },
      "encoding": {
        "x": {
          "field": "Trimestre",
          "type": "nominal"
        },
        "y": {
          "field": "Proportion",
          "type": "quantitative"
        },
        "text": {
          "field": "Banco/Grupo",
          "type": "nominal"
        },
        "color": {
          "field": "Banco/Grupo",
          "type": "nominal"
        }
      }
    }
  ],
  "config": {
    "view": {"stroke": null}
  }
}
