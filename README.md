# Visit https://github.com/lowlighter/metrics#-documentation for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          # The following scopes are required:
          #  - public_access (default scope)
          # The following additional scopes may be required:
          #  - read:org      (for organization related metrics)
          #  - read:user     (for user related data)
          #  - read:packages (for some packages related data)
          #  - repo          (optional, if you want to include private repositories)
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: hosseinshahabadi
          template: classic
          base: header, activity, community, repositories, metadata
          config_timezone: Asia/Tehran
          plugin_achievements: yes
          plugin_achievements_display: compact
          plugin_achievements_secrets: yes
          plugin_achievements_threshold: X
          plugin_introduction: yes
          plugin_introduction_title: yes
          plugin_isocalendar: yes
          plugin_isocalendar_duration: full-year
          plugin_leetcode: yes
          plugin_leetcode_limit_recent: 2
          plugin_leetcode_limit_skills: 10
          plugin_leetcode_sections: solved
          plugin_leetcode_user: .user.login
