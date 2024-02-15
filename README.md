# Pbx3cxFetchAndStoreBackups

Pbx3cxFetchAndStoreBackups is a robust solution designed to seamlessly fetch backups from 3CX hosts and securely store them on a SFTP server, maintaining a 7-day retention period.

## Overview

The project employs a collection of bash scripts tailored to address the specific backup needs of 3CX resellers, especially as the number of 3CX hosts continues to grow. By locally generating backups on 3CX hosts and transferring them securely to designated storage, this solution ensures data integrity and accessibility while simplifying the backup management process.

## Key Features

- Local Backup Generation: Backups are created locally on 3CX hosts, eliminating the need for the host to access the backup location.
- Secure Transfer: Utilises SSH key authentication for secure access to both 3CX hosts and the final backup destination.
- Retention Management: Maintains a 7-day retention period for each 3CX host, ensuring data availability for recovery purposes.
- Automated Reporting: Daily email reports provide technicians with valuable insights into backup status and performance.

## Setup

1. Configuration File: Rename .env.example to .env and customise it according to your specific requirements.
2. SSH Key Authentication: Ensure that the worker has SSH key access to both 3CX hosts and the designated backup storage.

## Scripts

### fetch_backups_parallel

Fetches backup files from 3CX hosts and stores them locally on the worker.

### store_backups_parallel

Transfers backup files from the worker to the designated storage location.
We usually rely on [Hetzner Storage Sox solution](https://www.hetzner.com/storage/storage-box/) for seamless accessibility via SCP or SFTP.

### check_backups

Verifies the integrity and freshness of backups, considering them valid if the file exists and was created within the last 24 hours.

### notify

Sends daily reports to designated technicians, configurable through the .env configuration file.

## Usage

To initiate backup fetching and storage processes, execute the relevant scripts with appropriate parameters. Ensure that the .env file is properly configured before running any scripts.

## Contribution

Contributions and feedback are welcome! Feel free to submit issues or pull requests to enhance the functionality and usability of the project.

## License

This project is licensed under the [GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.en.html), allowing users to freely use, modify, and distribute the software in compliance with the terms specified by the GPL-3.0 license agreement.
